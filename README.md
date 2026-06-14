# IA2Bimestre
README
Disciplina de Inteligência Artificial , Professor Munif , Unicesumar 2026

## Integrantes
- Amanda Lorena Ferreira Silverio - RA: 23130634-2
- Ana Clara Paim Lázaro - RA: 23087481-2
- Brenda Kethleen Cirqueira Lucas - RA: 23103459-2

---

## 4.2 Resumo do Projeto

### Contextualização do Tema
Na indústria vinícola, a classificação e a determinação da qualidade ou origem de um vinho dependem fortemente de análises químicas complexas (como teor alcoólico, acidez, magnésio e flavonoides). Tradicionalmente, essa validação exige especialistas e testes demorados. A aplicação de Inteligência Artificial surge como uma alternativa automatizada para identificar o tipo ou cultivar do vinho instantaneamente a partir de sua assinatura química.

### Problema Investigado
O desafio consiste em mapear 13 características físico-químicas de diferentes amostras de vinhos e determinar, com precisão, a qual de 3 classes (cultivares específicos) aquela amostra pertence. Trata-se de um problema clássico de **classificação multiclasse** de dados tabulares.

### Hipótese da Equipe
A hipótese inicial do grupo é que os modelos de Inteligência Artificial conseguirão identificar os padrões químicos dos vinhos com alta precisão. Espera-se que a **Rede Neural (MLP)**, por processar os atributos de forma combinada e não-linear, atinja uma taxa de acerto ligeiramente superior à da **Árvore de Decisão**, embora a Árvore ofereça uma leitura de regras muito mais simples e compreensível para humanos.

### Descrição do Dataset Utilizado
* **Nome:** Wine Recognition Dataset (Originário do UCI Machine Learning Repository).
* **Acesso:** Carregado diretamente via biblioteca `sklearn.datasets`.
* **Quantidade de Amostras:** 178 registros de vinhos.
* **Atributos (13 características preditoras):** Alcohol, Malic acid, Ash, Alcalinity of ash, Magnesium, Total phenols, Flavanoids, Nonflavanoid phenols, Proanthocyanidins, Color intensity, Hue, OD280/OD315 of diluted wines e Proline.
* **Variável Alvo (Target):** Classe do vinho (Classe 0, Classe 1 ou Classe 2).
* **Tratamento de Dados:** Os dados foram divididos em **70% para treinamento** e **30% para teste**. Para o modelo de Rede Neural (MLP), os atributos passaram por uma padronização estatística (`StandardScaler`), centralizando a média em 0 e desvio padrão em 1, garantindo o equilíbrio dos pesos na rede.

### Métodos de IA Utilizados
1. **Parte 1 (1º Bimestre): Árvore de Decisão (*Decision Tree Classifier*)**
   * Configuração: Limitada a uma profundidade máxima de 3 níveis (`max_depth=3`) para evitar o sobreajuste (*overfitting*) e manter o modelo visualmente explicável.
2. **Parte 2 (2º Bimestre): Rede Neural Perceptron Multicamadas (*MLP Classifier*)**
   * Configuração: Uma camada oculta contendo 10 neurônios (`hidden_layer_sizes=(10,)`) e limite de 500 épocas de treinamento (`max_iter=500`).

---

## 5. Avaliação dos Modelos e Resultados

*(Nota da equipe: Lembrem-se de salvar as imagens geradas pelo Google Colab e salvá-las na mesma pasta do repositório no GitHub, inserindo os links delas nos campos indicados abaixo)*

### Gráficos Obrigatórios

#### 1. Matrizes de Confusão
As matrizes mostram onde cada modelo acertou e onde confundiu as classes de vinhos.

* **Matriz de Confusão - Árvore de Decisão:**
  ![Matriz de Confusão - Árvore](<img width="493" height="407" alt="Matriz de Confusão - Árvore de Decisão" src="https://github.com/user-attachments/assets/ae499e63-9ce0-4af6-a8d0-1943d8f573ed" />

* **Matriz de Confusão - Rede Neural MLP:**
  ![Matriz de Confusão - MLP](<img width="496" height="409" alt="Matriz de Confusão - Rede Neural MLP" src="https://github.com/user-attachments/assets/75ca7c19-2704-42b6-ba8c-bfbba1bd41a3" />

#### 2. Curva de Perda (Loss Curve) da MLP
Demonstra o erro decrescendo a cada época, provando que a Rede Neural aprendeu com o algoritmo de Retropropagação (*Backpropagation*).
![Curva de Perda - MLP](<img width="619" height="422" alt="Curva de Perda Durante o Treinamento" src="https://github.com/user-attachments/assets/d2a26bab-76a3-4f7d-adb9-4a4721c84691" />

#### 3. Comparação Gráfica entre Modelos
Gráfico final que consolida o desempenho das duas arquiteturas sobre a base de teste.
![Comparação de Acurácia](<img width="619" height="407" alt="Comparação Direta de Desempenho" src="https://github.com/user-attachments/assets/cd331c92-92f9-4ac8-a1c4-ab02915d54bd" />

---

### Comparação dos Resultados e Análise Crítica

Abaixo estão resumidas as principais métricas obtidas por cada algoritmo durante a validação:

| Modelo | Acurácia Geral | Vantagens | Desvantagens |
| :--- | :---: | :--- | :--- |
| **Árvore de Decisão** | 96.30% | Alta explicabilidade; regras visuais simples; não exige normalização de dados. | Rigidez nas fronteiras de decisão (regras quadradas/binárias). |
| **Rede Neural (MLP)** | 98.15% | Maior precisão; mapeia relações complexas entre vários atributos químicos ao mesmo tempo. | Efeito "caixa-preta" (baixa explicabilidade); exige padronização prévia dos dados. |

Analisando criticamente o desempenho, a **Rede Neural (MLP) obteve a melhor performance**, alcançando uma acurácia de **98.15%** contra **96.30%** da Árvore de Decisão. 

Essa diferença ocorre porque a Árvore de Decisão analisa os atributos isoladamente a cada nó por meio de cortes rígidos, enquanto a MLP combina as 13 variáveis de entrada simultaneamente através de seus neurônios artificiais e funções de ativação. Contudo, dado o alto desempenho de ambos, a Árvore de Decisão se destaca como uma alternativa viável por ser computacionalmente mais leve e fácil de auditar.

---

## Conclusão

O projeto cumpriu com êxito todas as etapas de uma solução real em Ciência de Dados e IA. A hipótese da equipe foi confirmada: a Rede Neural MLP de fato superou a Árvore de Decisão em capacidade preditiva no *Wine Dataset*. 

O desenvolvimento deste trabalho permitiu consolidar a diferença prática entre os modelos clássicos baseados em regras (1º Bimestre) e os modelos bio-inspirados baseados em conexões e ajustes de pesos sinápticos (2º Bimestre), evidenciando o equilíbrio necessário entre a busca por maior precisão (MLP) e a necessidade de clareza e explicabilidade do modelo (Árvore).
