# Atividade Prática: Projeto de sistema para filtragem digital em ponto-fixo

O projeto é um sistema para filtragem digital utilizando representação de números em ponto fixo.

A equipe tem liberdade para adotar as estruturas clássicas já discutidas em sala de aula, ou aprofundar o assunto em livros-texto como os de Richard G. Lyons ("Understanding Digital Signal Processing") e Oppenheim & Schafer ("Discrete-Time Signal Processing"), e artigos clássicos como os de Mullis & Roberts e Jackson (são artigos antigos e relativamente complexos). De fato, otimizar projeto de FIR e IIR com comprimento de palavra finito é a alocação não uniforme de bits por coeficiente, onde diferentes coeficientes, ou mesmo diferentes seções, recebem diferentes números de bits para minimizar a sensibilidade ou o ruído de arredondamento sob um orçamento fixo de hardware.

## 1. Objetivo da Atividade
O objetivo é maximizar a razão sinal/ruído (SNR) entre o sinal filtrado e o original, através da atenuação do ruído e da interferência de uma única forma de onda de EEG. O ruído é do tipo AWGN ("ruído aditivo, branco e Gaussiano") e a interferência está em 60 Hz. Assume-se que a banda de frequência de interesse na análise de EEG é de 0 a 40 Hz. O sistema deve ser capaz de processar vários canais de EEG em tempo real.

O "hardware" considerado é um processador DSP que utiliza um acumulador (acc) de 16 bits com saturação implementada, e todos os outros números são representados em 8 bits.O projetista tem permissão para trabalhar com os seguintes graus de liberdade:

1. Qualquer representação em ponto fixo pode ser utilizada, desde que sejam usados apenas números de 8 bits, com exceção do acumulador (acc) de 16 bits. Em outras palavras, as restrições de hardware assumidas devem ser respeitadas. Mas o projetista pode usar a representação Q2.5 em algum ponto do fluxo (pipeline) do DSP e Q3.4 em outro, por exemplo.

2. Qualquer ordem de filtro pode ser utilizada, bem como qualquer implementação (forma direta, seções SOS, etc.).

3. Caso a equipe investigue estruturas avançadas como "mutiplierless filters" (veja, por exemplo, https://arxiv.org/pdf/1912.04210), "sparse FIR filters" (https://ieeexplore.ieee.org/document/9362902) ou "filters with powers-of-two coefficients" (https://ieeexplore.ieee.org/document/1096001), pode eventualmente modificar o método check_realtime_difference_equation() para que reflita adequadamente o custo computacional da estrutura avançada. O método check_realtime_difference_equation() assume implementações convencionais de H(z) e não dá suporte a várias estruturas avançadas.

3. A equipe pode modificar métodos como apply_fixed_point_filter_int8() para refletir a quantização e estrutura de filtragem adotadas.

4. A principal métrica da qualidade da filtragem é a SNR exemplificada na célula com o título "Final comparison to get SNR". Por exemplo, para o filtro IIR de exemplo, tem-se o resultado SNR = 2.60 dB. O objetivo do projeto é criar um sistema que, obedecendo às restrições, maximize essa SNR entre o resultado final da filtragem e o sinal original, antes de se adicionar ruído e interferência.

5. É frequentemente vantajoso usar formatos de ponto fixo diferentes Qm.n para os coeficientes do numerador B(z) e do denominador A(z). Não há nenhuma exigência de que todos os coeficientes compartilhem o mesmo formato Q.

6. Os coeficientes do denominador são muito mais críticos pois uma pequena perturbação em um coeficiente de A(z) desloca os pólos, potencialmente causando instabilidade e grandes distorções na resposta em frequência. Os coeficientes do numerador afetam apenas os zeros, que geralmente são muito menos sensíveis. Por exemplo, em implementações em FPGA é comum usar coeficientes de B(z) usando-se 12 a 16 bits, enquanto os de A(z) usam 18 a 24 bits.

7. Em implementações em cascata de SOS (seções de segunda ordem), cada seção pode ter seu próprio formato de coeficiente Qm.n. Outra técnica usada é fazer o pareamento de pólos e zeros para que cada SOS, além da escolha da ordem das seções.

8. Se a implementação calcula a_k * y[n−k] e b_k * x[n−k] com diferentes comprimentos fracionários, esses produtos devem eventualmente ser alinhados a uma escala comum (uma mesma posição do ponto binário) antes de serem acumulados. Portanto, o formato do acumulador interno deve acomodar ambos os conjuntos de produtos.

Cada equipe deve então projetar e simular o sistema de filtragem digital. Usando o método check_realtime_difference_equation() (ou customização adequada) e sem modificar o valor de ```number_of_channels = 140```, deve-se garantir que o sistema é apto a executar em tempo real.

**Restrição:**

1. O sistema deve maximizar a SNR citada, mas ser apto a executar, em tempo real, o número de canais de EEG especificado.

2. A equipe não pode modificar o sinal de entrada, incluindo ruído e interferência que são adicionados, ou sua quantização.


---

## 2. Dinâmica de Grupo
* Esta atividade será realizada em **grupo** de no máximo 4 pessoas.

---

## 3. Entregáveis
Os grupos devem entregar:
1. **Notebook (.ipynb):** Código documentado com os testes, gráficos e a solução final otimizada.
2. **Relatório Técnico (Artigo):** Documento de no máximo 3 páginas seguindo o formato SBRT (escrita simples e direta), mantendo o padrão de redação científica.
3. **Apresentação:** Defesa técnica da solução (slides). Todos da equipe devem saber o código usado. A nota é individual.

---

## 4. Requisitos do Relatório (Conteúdo Obrigatório)
O relatório deve ser focado em dados técnicos e cálculos claros. Deve justificar as escolhas feitas.

---

## 5. Instruções para o Google Colab
Caso esteja a utilizar o notebook via GitHub:
* As alterações **não são salvas** automaticamente no link original.
* Vá em **Ficheiro > Guardar uma cópia no Drive** para salvar o progresso na sua conta Google.
* Ou use **Ficheiro > Transferir > Transferir .ipynb** para guardar o ficheiro no seu computador.
