# Aula: Análise AC sobre a Polarização DC do Transistor BJT

## 1. Por que analisar sinal AC sobre o sinal DC?

Porque a análise DC responde apenas **onde o transistor opera**, enquanto a análise AC responde **como ele amplifica**.

### Nós já resolvemos o circuito. Ou não?

Considere o circuito abaixo já polarizado:

* VB = 1,6V
* VE = 0,9V
* VC = 5,3V
* VCE = 5,8V
* IC = 1mA


> Se eu aplicar um sinal senoidal de 100 mV na entrada, qual será a amplitude do sinal na saída?

* Qual seria o novo VCE?
* Qual seria o novo IC?
* Saberia verificar se está na região ativa?

Porém, esses cálculos não conseguem determinar:

* ganho
* amplitude de saída
* inversão de fase

### O que a análise DC realmente nos entrega?

**A análise DC responde apenas metade da história**

### Tabela

| Pergunta                   | DC responde? |
| -------------------------- | ------------ |
| Transistor está ligado?    | ✔            |
| Está na região ativa?      | ✔            |
| Qual o ponto Q?            | ✔            |
| Qual o ganho?              | ✖            |
| Qual a amplitude da saída? | ✖            |
| Há inversão de fase?       | ✖            |


### Conclusão

> A análise DC posiciona o transistor, mas não descreve o comportamento do sinal.

### O papel do ponto Q

**Então por que calculamos o ponto Q?**

Lembra da reta de carga?

* Região de Corte
* Região Ativa
* Região de Saturação
* Logo, encontra o Ponto Q que é o centro da Reta de Carga.

> **O ponto Q não existe para amplificar. Ele existe para preparar o transistor para amplificar.**
> **É como ajustar a posição inicial de um elevador. Antes de movimentá-lo para cima e para baixo, ele precisa estar parado em um andar adequado.**


# 2. Surge um novo problema

**Agora o sinal começa a variar**

```text
DC → valor fixo

AC → valor variável
```

Exemplo:

```text
Base = 1,60 V  (DC)

Sinal = ±100 mV (AC)
```

Resultado:

```text
1,5 V ↔ 1,7 V
```

```text
1,70 V  ─────╮    ╭─────
             │╲  ╱│
1,60 V  ─────┼─\/─┼─────
             │    │
1,50 V  ─────╯    ╰─────
```

### Pergunta

> **O que acontece com a corrente do transistor quando a tensão da base oscila alguns milivolts ao redor do ponto Q?**

> **Para responder essa pergunta precisamos abandonar temporariamente a análise DC e enxergar o transistor de uma forma completamente diferente: como um dispositivo de pequenos sinais.**

```text
Análise DC
↓
Encontra o ponto Q
↓
Define a corrente IE
↓
Determina o valor de re
↓
Permite criar o modelo AC
↓
Calcula o ganho do amplificador
```

> **A polarização DC não é o fim da análise. Ela é apenas o ponto de partida da análise AC.**

> O pulo do gato da aula de hoje é entender o **re** = resistência dinâmica.


# 3. Separando DC e AC

### Tópicos

* Componente DC
* Componente AC
* Sinal total

### Matemática

Vtotal = VDC + VAC

### Conceito

O transistor enxerga:

* um valor médio (DC)
* uma pequena variação (AC)

simultaneamente.


# 4. O que significa Pequenos Sinais?

- Uma aproximação linear.

### Tópicos

* Curva exponencial da junção BE
* Operação ao redor do ponto Q
* Linearização local

### Visual

Curva exponencial + zoom no ponto Q.

### Conclusão

> A análise AC observa apenas a vizinhança do ponto de operação.


# 5. De onde surgem os 26 mV?

- Dar significado físico ao modelo.

### Tópicos

* Tensão térmica

V_T=\frac{kT}{q}

* Temperatura ambiente

VT≈ 26mV

### Conclusão

> Os 26 mV são uma constante física da junção PN.

# 6. O que é o (re)?

### Objetivo

Construir o conceito central da aula.

### Tópicos

* Resistência dinâmica
* Não é um resistor físico
* Inclinação da curva do diodo

### Fórmula

r_e=\frac{26mV}{I_E}

### Experimento mental

Comparar:

* (I_E=0,5mA)
* (I_E=5mA)

e observar a mudança em (r_e).

---

# 7. Ligação entre Polarização DC e Ganho AC

### Objetivo

Fazer o "clique" conceitual.

### Construção

[
I_E
]

↓

[
r_e
]

↓

[
A_v
]

### Mensagem

> O ganho nasce da polarização.

---

# 8. Como transformar um circuito DC em AC

### Objetivo

Ensinar o procedimento padrão.

### Passos

#### Passo 1

Resolver a polarização DC.

#### Passo 2

Eliminar (V_{CC}).

#### Passo 3

Curto-circuitar capacitores.

#### Passo 4

Inserir o modelo de pequenos sinais.

---

# 9. Modelo re do transistor

### Objetivo

Apresentar o modelo equivalente.

### Tópicos

* (\beta r_e)
* fonte de corrente controlada
* conceito de impedância de entrada

### Mostrar

Modelo equivalente simplificado do emissor comum.

---

# 10. Ganho de tensão

### Objetivo

Chegar à primeira equação importante.

### Fórmula

A_v\approx-\frac{R_C}{r_e}

### Discutir

* inversão de fase
* influência de (R_C)
* influência de (r_e)

---

# 11. Exemplo Completo

### Objetivo

Conectar tudo.

### Dados

* (V_{CC})
* (R_1)
* (R_2)
* (R_C)
* (R_E)
* (\beta)

### Resolver

1. Polarização DC
2. (I_E)
3. (r_e)
4. Modelo AC
5. Ganho

---

# 12. Simulação LTspice

### Objetivo

Validar teoria.

### Medidas

* Entrada (CH1)
* Saída (CH2)

### Comparar

[
A_v=\frac{V_o}{V_i}
]

medido versus calculado.

---

# 13. Fechamento

### Síntese final

Mostre apenas este fluxo:

```text
Polarização DC
      ↓
   Ponto Q
      ↓
     IE
      ↓
     re
      ↓
 Modelo AC
      ↓
 Ganho Av
```

Essa estrutura costuma ocupar entre **2h e 3h de aula**, dependendo do tempo dedicado ao exemplo numérico e à simulação. O ponto central é que o aluno saia entendendo que **a análise AC não substitui a análise DC; ela depende completamente dela**.





Essa seção é crucial porque é nela que os alunos entendem por que podemos "ignorar" a fonte (V_{CC}) e substituir capacitores por curtos na análise AC. Se essa parte ficar bem consolidada, o restante da aula flui naturalmente.

---

# 3. Separando DC e AC

## Objetivo da Seção

Levar os estudantes a compreender que:

* o transistor opera simultaneamente com sinais DC e AC;
* cada componente exerce uma função diferente;
* podemos analisar cada contribuição separadamente usando o princípio da superposição.

---

# Slide 1 — O transistor vê duas coisas ao mesmo tempo

### Título

**O transistor recebe dois sinais simultaneamente**

### Diagrama

Mostrar:

```text
       Sinal AC
           ~
           │
           ▼

      +---------+
      |  BJT    |
      +---------+
           ▲
           │

      Polarização DC
```

---

### Explicação

Pergunte:

> "Quando ligamos um amplificador de áudio, o transistor recebe apenas a música?"

Normalmente alguém responderá que não.

Continue:

> "Além da música, existe uma rede de polarização mantendo o transistor na região ativa."

Portanto:

```text
Polarização DC
+
Sinal AC
=
Sinal total aplicado
```

---

### Mensagem principal

> O transistor nunca vê apenas o sinal AC. Ele vê o sinal AC somado ao nível DC de polarização.

---

# Slide 2 — O sinal real na base

### Título

**O que realmente chega à base do transistor?**

Apresente:

```text
Polarização DC = 1,80 V

Sinal AC = ±50 mV
```

Então mostre:

```text
VB(t) = 1,80V + Vac(t)
```

---

### Exemplo visual

```text
1,85 V  ─────╮    ╭─────
             │╲  ╱│
1,80 V  ─────┼─\/─┼─────
             │    │
1,75 V  ─────╯    ╰─────
```

---

### Explicação

Mostre que:

* a senoide não oscila em torno de 0 V;
* ela oscila em torno do ponto de polarização.

---

### Pergunta

> "O transistor amplifica os 1,80 V ou apenas os 50 mV que estão variando?"

Deixe a turma discutir.

---

# Slide 3 — O que realmente interessa para amplificar?

### Título

**O transistor responde às variações**

Mostre dois casos:

### Caso 1

```text
1,80 V constante
```

Resultado:

```text
IC constante
```

---

### Caso 2

```text
1,80 V + senoide
```

Resultado:

```text
IC variável
```

---

### Conclusão

> O componente DC mantém o transistor ligado.
>
> O componente AC produz a variação de corrente responsável pela amplificação.

---

# Slide 4 — O princípio da superposição

### Título

**Podemos analisar DC e AC separadamente**

Introduza o conceito:

> Em circuitos lineares, a resposta total é a soma das respostas individuais.

---

### Mostrar

[
Resposta_{total}
================

Resposta_{DC}
+
Resposta_{AC}
]

---

### Aplicação ao transistor

Primeiro:

```text
Análise DC
↓
Determina o ponto Q
```

Depois:

```text
Análise AC
↓
Determina ganho e impedâncias
```

---

### Mensagem

> Embora ocorram simultaneamente, podemos estudá-las separadamente.

---

# Slide 5 — O truque da análise AC

### Título

**Como "removemos" a polarização DC?**

Pergunte:

> "Se queremos estudar apenas o comportamento AC, o que fazemos com a fonte DC?"

---

Mostre:

```text
VCC = constante
```

Para o sinal AC:

```text
não varia
```

Logo:

```text
equivale a terra AC
```

---

### Resultado

Na análise AC:

```text
VCC
↓
Curto-circuito
```

---

### Mensagem importante

> Não estamos desligando a fonte na vida real.
>
> Estamos apenas removendo sua influência da análise AC.

---

# Slide 6 — O papel dos capacitores

### Título

**Por que os capacitores viram curtos?**

Mostrar:

[
X_C=\frac{1}{2\pi f C}
]

Sem aprofundar.

---

### Explicação

Para frequências de operação:

* impedância muito pequena;
* sinal atravessa facilmente.

Portanto:

```text
Capacitor
↓
Curto-circuito AC
```

---

### Observação

Explique que:

* para DC → capacitor é aberto;
* para AC → capacitor é quase um fio.

Esse conceito costuma gerar vários "ahhh agora entendi".

---

# Slide 7 — Transformação do circuito

### Título

**Nascimento do circuito equivalente AC**

Mostrar uma sequência visual:

### Etapa 1

Circuito original.

### Etapa 2

Eliminar (V_{CC}).

### Etapa 3

Curto nos capacitores.

### Etapa 4

Circuito simplificado.

---

### Mensagem final da seção

> A análise DC nos entrega o ponto Q.
>
> A análise AC elimina as fontes DC e simplifica o circuito para estudar apenas as pequenas variações responsáveis pela amplificação.

---

# Fechamento da seção

Encerrar com este fluxo:

```text
Circuito Real
      ↓
Separar DC e AC
      ↓
Análise DC
      ↓
Encontrar IE
      ↓
Análise AC
      ↓
Determinar ganho
```

### Frase de transição para a próxima seção

> "Agora que conseguimos separar o sinal variável do sinal de polarização, surge uma nova pergunta: como o transistor reage a pequenas variações de tensão ao redor do ponto Q? É exatamente daí que nasce o conceito de pequenos sinais e a resistência dinâmica (r_e)."


