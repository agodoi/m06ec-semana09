# Aula: Análise AC sobre a Polarização DC do Transistor BJT

## 1. Por que analisar sinal AC sobre o sinal DC?

Porque a análise DC responde apenas **onde o transistor opera**, enquanto a análise AC responde **como ele amplifica**.

### Nós já resolvemos o circuito ou não?

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

**A análise DC responde apenas metade da história**. Veja a tabela:

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

### Perguntas:

> **O que acontece com a corrente do transistor quando a tensão da base oscila alguns milivolts ao redor do ponto Q?**

> **Para responder essa pergunta precisamos abandonar temporariamente a análise DC e enxergar o transistor de uma forma completamente diferente: como um dispositivo de pequenos sinais.** Observe o fluxo abaixo que resume o que falei agora:

```text
Análise DC 							(autoestudos da aula passada)
↓
Encontra o ponto Q 					(autoestudos da aula passada)
↓
Define a corrente IE 				(autoestudos da aula passada)
↓
Determina o valor de re 			(veremos isso hoje)
↓
Permite criar o modelo AC 			(veremos isso hoje)
↓
Calcula o ganho do amplificador 	(veremos isso hoje)
```

> **A polarização DC não é o fim da análise. Ela é apenas o ponto de partida da análise AC.**

> O pulo do gato da aula de hoje é entender o **re** = resistência dinâmica.


# 3. Separando DC e AC. Tem jeito?


* Sim, é possível analisar separadamente;
* Embora, o transistor opere simultaneamente com sinais DC e AC;
* Cada componente exerce uma função diferente;
* Ao analisar cada contribuição separadamente, estamos usando o princípio da superposição.
* Em circuitos lineares, a resposta total é a soma das respostas individuais.

> **O transistor nunca vê apenas o sinal AC. Ele vê o sinal AC somado ao nível DC de polarização.**

> 1,60 V + senoide, o resultado será IC variável.

### Matemática

Vtotal = VDC + VAC

### Como removemos o sinal DC no Princípio da Superposição?

* Fonte DC passa a ser um curto no circuito do ponto de vista do AC. Isto é, simplesmente é eliminado do circuito;
* Capacitor também passa a ser um curto quando se tem frequência AC;
* XC​=1 / 2πfC​

> **Agora que conseguimos separar o sinal variável do sinal de polarização, surge uma nova pergunta: como o transistor reage a pequenas variações de tensão ao redor do ponto Q? É exatamente daí que nasce o conceito de Pequenos Sinais e a Resistência Dinâmica re**
	​

# 4. O que significa Pequenos Sinais?

- O transistor não se comporta como um resistor;
- Logo, o transistor é um dispositivo **não linear**. Lembre-se da curva do diodo? É uma exponencial. O transistor é feito de 2 diodos internamente;

> **Se eu dobrar VBE, a corrente IC ou IE dobra?**
	​
- Porém, próximo ao ponto Q, ele pode ser aproximado por um circuito linear;
- De longe, a curva é uma exponencial, mas de perto, é uma reta. Se você fosse uma formiga no ponto Q, andando 10mV para cima e para baixo, é praticamente uma reta;
- Essa aproximação é a base de toda a análise AC de pequenos sinais.

> **Pequenos sinais observam apenas um trecho muito pequeno da curva.**

### Conclusão

> **A análise AC observa apenas a vizinhança do ponto de operação.**

* Toda reta possui uma inclinação
* Se a curva local parece uma reta: R= ΔI / ΔV (Lei de Ohm)
* Então R = ΔVBE / ΔIE

> **Esse R é o re. Resistência Dinâmica.**
> Logo, re = ΔVBE / ΔIE
	​
- O **re** mede a sensibilidade da corrente do emissor a pequenas variações da tensão base-emissor.

> Quanto menor o **re**, mais facilmente o transistor converte pequenas variações de tensão em variações de corrente.


# 5. Como faço para encontrar re?

### Matematicamente

> re = 26mV / IE

### De onde surge esses 26 mV?

* Tensão térmica: VT=k*T / q
	* k Constante de Boltzmann, k=1,38×10−23 J/K;
	* T = temperatura ambiente em Kelvin;
	* q = carga de um único elétron, q = 1,602×10−19 C
* Fazendo a conta: VT​=(1,38×10−23) * (298) / 1,602×10−19​
* VT≈ 26mV

### Conclusões

> A tensão térmica não é uma tensão aplicada. Ninguém conecta uma fonte de 26 mV ao transistor.
> Ela representa o efeito da temperatura sobre o movimento dos portadores dentro do semicondutor.
> Os 26 mV são uma constante física da junção PN.
> 0,7 V: Valor aproximado necessário para polarizar a junção base-emissor.
> 26 mV: Constante física associada à temperatura que determina quão sensível ele fica depois que já está ligado.




### Experimento mental

Comparar:

* (I_E=0,5mA)
* (I_E=5mA)

e observar a mudança em re.

| Situação | (I_E)  | (r_e) | (\Delta I_E) para 10 mV |
| -------- | ------ | ----- | ----------------------- |
| Caso A   | 0,5 mA | 52 Ω  | 0,19 mA                 |
| Caso B   | 5 mA   | 5,2 Ω | 1,92 mA                 |

> **Qual dos dois transistores responde mais fortemente ao mesmo sinal de entrada?**

```
IE ↑
↓
re ↓
↓
ΔIE ↑
↓
Ganho ↑
```
> **Quando aumentamos a corrente de polarização, a junção fica mais sensível às pequenas variações do sinal. O transistor não mudou. O que mudou foi o ponto Q.**

# X. Construindo o Modelo AC do Transistor

# 9. Modelo re do transistor

* Agora que descobrimos o que é o re, onde exatamente ele aparece no circuito?
* Transformando um BC548 em um modelo equivalente e simplificado.

### Transforme o BC548 em um modelo equivalente

* Junção BE → é complicado de transformar isso num modelo
* Junção BC → idem
* Regiões N e P → é foda
* Portadores de carga → é mais ainda

Solução:

> **Para pequenos sinais: β*re**​ e vamos chamar isso de **ENTRADA**
> **fonte de corrente controlada: IC​=β*IB**​ e vamos chamar isso de **SAÍDA**
> O transistor desaparece e é substituído por elementos que reproduzem seu comportamento para pequenos sinais na **ENTRADA** e na **SAÍDA**.

### Conclusões

* Zi​≈β*re​
* Exemplo: β=100, re=10Ω, logo: Zi =1000Ω
* Por isso que alguns MP3 players são melhores que outros ao conectar no seu amplificador. Isso chama-se casamento de impedância.
* Quando o seu MP3 player possui uma saída próxima do Zi do seu Amplificador, o desempenho é maior devido ao conceito de **Máxima Transferência de Potência** (MTP).

> **Embora a junção tenha apenas 10 Ω, olhando pela base enxergamos aproximadamente 1 kΩ.**

```
Vi
↓
Ib
↓
Ic = βIb
↓
RC
↓
Vo
```

* Que é o mesmo que:

```
Entrada
   ↓
 βre
   ↓
Fonte controlada
   ↓
Saída
```

* Mais uma conclusão

```
Polarização DC
      ↓
IE
      ↓
re
      ↓
Modelo AC
      ↓
Av
```

> **Agora que o transistor foi substituído por um circuito equivalente, finalmente temos todas as ferramentas para calcular o ganho do amplificador.**

# X. Ganho de tensão

### Fórmula

> 𝐴𝑣  ≈ −𝑅𝐶 / 𝑟𝑒
​​
PAREI AQUI
>
> 
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



### Frase de transição para a próxima seção

> "Agora que conseguimos separar o sinal variável do sinal de polarização, surge uma nova pergunta: como o transistor reage a pequenas variações de tensão ao redor do ponto Q? É exatamente daí que nasce o conceito de pequenos sinais e a resistência dinâmica (r_e)."


