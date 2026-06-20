# Atividade Prática: Projeto de sistema para filtragem digital em ponto-fixo

## 1. Objetivo da Atividade
O projeto é um sistema para filtragem digital utilizando representação de números em ponto fixo. O objetivo é atenuar o ruído e a interferência de uma única forma de onda de EEG. O ruído é do tipo AWGN ("ruído aditivo, branco e Gaussiano") e a interferência está em 60 Hz. Assume-se que a banda de frequência de interesse na análise de EEG é de 0 a 40 Hz. O sistema deve ser capaz de processar vários canais de EEG em tempo real.

O "hardware" considerado é um processador DSP que utiliza um acumulador (acc) de 16 bits com saturação implementada, e todos os outros números são representados em 8 bits.O projetista tem permissão para trabalhar com os seguintes graus de liberdade:

1. Qualquer representação em ponto fixo pode ser utilizada, desde que sejam usados apenas números de 8 bits, com exceção do acumulador (acc) de 16 bits. Em outras palavras, as restrições de hardware assumidas devem ser respeitadas. Mas o projetista pode usar a representação Q2.5 em algum ponto do fluxo (pipeline) do DSP e Q3.4 em outro, por exemplo.

2. Qualquer ordem de filtro pode ser utilizada, bem como qualquer implementação (forma direta, seções SOS, etc.).

**Restrição:** O sistema deve ser apto a executar, em tempo real, o número de canais de EEG especificado.

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
