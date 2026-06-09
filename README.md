# Aula: Análise AC sobre a Polarização DC do Transistor BJT

## 1. Motivação: Por que fazer mais cálculos?

### Objetivo da Seção

Perceberem que a análise DC responde apenas **onde o transistor opera**, enquanto a análise AC responde **como ele amplifica**.

### Nós já resolvemos o circuito. Ou não?

Considere o circuito abaixo já polarizado:

* VB = 1,8V
* VE = 1,1V
* VC = 6,2V
* IC = 1mA
* VCE = 5,1V

> Se eu aplicar um sinal senoidal de 100 mV na entrada, qual será a amplitude do sinal na saída?

* Sabe calcular VCE?
* sabe calcular (IC?
* sabe verificar a região ativa?

Se sabe, beleza, caso não, precisa voltar nos autoestudos da aula anterior. Porém, esses cálculos não conseguem determinar:

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
* Região ativa
* Região de Saturação
* Ponto Q

> "O ponto Q não existe para amplificar. Ele existe para preparar o transistor para amplificar."

### Analogia

> "É como ajustar a posição inicial de um elevador. Antes de movimentá-lo para cima e para baixo, ele precisa estar parado em um andar adequado."


# Surge um novo problema

**Agora o sinal começa a variar**

```text
DC → valor fixo

AC → valor variável
```

Exemplo:

```text
Base = 1,80 V  (DC)

Sinal = ±50 mV (AC)
```

Resultado:

```text
1,75 V ↔ 1,85 V
```

### Pergunta

> O que acontece com a corrente do transistor quando a tensão da base oscila alguns milivolts ao redor do ponto Q?

---

### Gancho para o próximo tópico

> "Para responder essa pergunta precisamos abandonar temporariamente a análise DC e enxergar o transistor de uma forma completamente diferente: como um dispositivo de pequenos sinais."

---

# Fechamento da seção

Finalize com um único slide de síntese:

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

### Frase final

> "A polarização DC não é o fim da análise. Ela é apenas o ponto de partida da análise AC."

Essa abertura normalmente leva de **10 a 15 minutos** e prepara perfeitamente o terreno para introduzir **pequenos sinais, tensão térmica (26 mV) e resistência dinâmica (r_e)**.






# 2. Revisão rápida do ponto Q

### Tópicos

* Região de corte
* Região ativa
* Região de saturação
* Ponto de operação (Q)

### Conclusão

> O ponto Q não amplifica nada. Ele apenas posiciona o transistor para amplificar.


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


