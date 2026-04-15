# Atividade Prática: Otimização de Sinais para Classificação com IA

## 1. Objetivo da Atividade
O objetivo é projetar um estágio de pré-processamento (front-end DSP) para preparar sinais que serão classificados por um modelo de Machine Learning (ML). O desafio é reduzir ao máximo o tamanho dos dados (memória e processamento), mantendo a precisão da classificação em níveis aceitáveis.

Você deve encontrar o equilíbrio ideal entre:
1. **Fator de Decimação:** Redução da taxa de amostragem.
2. **Quantização:** Definição da profundidade de bits e tipo de quantizador (uniforme ou não-uniforme).

**Restrição:** O modelo de classificação de ML é fixo e não pode ser alterado. Todo o ganho de eficiência deve vir do tratamento de sinais.

---

## 2. Dinâmica de Grupo
* Esta atividade será realizada em **grupo**. 
* A quantidade de integrantes por grupo será definida em sala pelo professor e, posteriormente, este documento será atualizado com o número oficial.

---

## 3. Entregáveis
Os grupos devem entregar:
1. **Notebook (.ipynb):** Código documentado com os testes, gráficos e a solução final otimizada.
2. **Relatório Técnico (Artigo):** Documento de 3 páginas seguindo o formato SBRT (escrita simples e direta).
3. **Apresentação:** Defesa técnica da solução (slides).

---

## 4. Requisitos do Relatório (Conteúdo Obrigatório)
O relatório deve ser focado em dados técnicos e cálculos claros, incluindo:
* **Parâmetros de Decimação:** Justificar o fator escolhido e demonstrar o impacto na largura de banda do sinal.
* **Projeto de Quantização:** Detalhar se foi usado quantizador uniforme ou não-uniforme (ex: Mu-law) e por quê.
* **Cálculos de Consequências:** * Apresentar obrigatoriamente o **cálculo do erro de quantização**.
    * Discutir a relação sinal-ruído de quantização (SQNR) obtida.
* **Análise de Desempenho:** Mostrar a relação entre a compressão dos dados (armazenamento poupado) e a perda (ou manutenção) da acurácia do classificador.

---

## 5. Fluxo de Trabalho (Pipeline)
1. **Representação:** Aplicar decimação e redução de bits nos dados brutos.
2. **Classificação:** Passar os dados reduzidos pelo classificador.
3. **Análise de Erro:** Calcular o erro introduzido pelo processamento digital.
4. **Otimização:** Repetir o processo para encontrar a menor pegada de dados com a maior acurácia possível.

---

## 6. Instruções para o Google Colab
Caso esteja a utilizar o notebook via GitHub:
* As alterações **não são salvas** automaticamente no link original.
* Vá em **Ficheiro > Guardar uma cópia no Drive** para salvar o progresso na sua conta Google.
* Ou use **Ficheiro > Transferir > Transferir .ipynb** para guardar o ficheiro no seu computador.
