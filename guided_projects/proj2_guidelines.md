# Atividade Prática: Projeto de sistema para filtragem digital em ponto-fixo

O projeto é um sistema para filtragem digital utilizando representação de números em ponto fixo.

## 1. Objetivo da Atividade
O objetivo é maximizar a razão sinal/ruído (SNR) entre o sinal filtrado e o original, através da atenuação do ruído e da interferência de uma única forma de onda de EEG. O ruído é do tipo AWGN ("ruído aditivo, branco e Gaussiano") e a interferência está em 60 Hz. Assume-se que a banda de frequência de interesse na análise de EEG é de 0 a 40 Hz. O sistema deve ser capaz de processar vários canais de EEG em tempo real.

O "hardware" considerado é um processador DSP que utiliza um acumulador (acc) de 16 bits com saturação implementada, e todos os outros números são representados em 8 bits.O projetista tem permissão para trabalhar com os seguintes graus de liberdade:

1. Qualquer representação em ponto fixo pode ser utilizada, desde que sejam usados apenas números de 8 bits, com exceção do acumulador (acc) de 16 bits. Em outras palavras, as restrições de hardware assumidas devem ser respeitadas. Mas o projetista pode usar a representação Q2.5 em algum ponto do fluxo (pipeline) do DSP e Q3.4 em outro, por exemplo.

2. Qualquer ordem de filtro pode ser utilizada, bem como qualquer implementação (forma direta, seções SOS, etc.).

3. Caso a equipe investigue estruturas avançadas como "mutiplierless filters" (veja, por exemplo, https://arxiv.org/pdf/1912.04210), "sparse FIR filters" (https://ieeexplore.ieee.org/document/9362902) ou "filters with powers-of-two coefficients" (https://ieeexplore.ieee.org/document/1096001), pode eventualmente modificar o método check_realtime_difference_equation() para que reflita adequadamente o custo computacional da estrutura avançada. O método check_realtime_difference_equation() assume implementações convencionais de H(z) e não dá suporte a várias estruturas avançadas.

3. A equipe pode modificar métodos como apply_fixed_point_filter_int8() para refletir a quantização e estrutura de filtragem adotadas.

4. A principal métrica da qualidade da filtragem é a SNR exemplificada na célula com o título "Final comparison to get SNR". Por exemplo, para o filtro IIR de exemplo, tem-se o resultado SNR = 2.60 dB. O objetivo do projeto é criar um sistema que, obedecendo às restrições, maximize essa SNR entre o resultado final da filtragem e o sinal original, antes de se adicionar ruído e interferência.

Cada equipe deve então projetar e simular o sistema de filtragem digital. Usando o método check_realtime_difference_equation() e sem modificar o valor de ```number_of_channels = 140```, deve-se garantir que o sistema é apto a executar em tempo real.

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
