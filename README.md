## **Classificação de Radiografias da Coluna Vertebral com Keras**

Este repositório contém uma implementação completa para classificar radiografias da coluna vertebral em três classes clínicas: **Normal**, **Escoliose (Scol)** e **Spondilolistese (Spond)**. O modelo utiliza o backbone **MobileNetV2** pré-treinado no ImageNet, ajustado com camadas personalizadas e treinado em duas fases (feature extraction e fine-tuning). A implementação é exclusivamente baseada na API moderna do **Keras**, garantindo simplicidade e eficiência.

---

## **Conteúdo**

1. [Visão Geral](#visão-geral)
2. [Requisitos](#requisitos)
3. [Estrutura do Projeto](#estrutura-do-projeto)
4. [Como Usar](#como-usar)
   - [Treinamento do Modelo](#treinamento-do-modelo)
   - [Inferência com Imagens](#inferência-com-imagens)
5. [Executar no Google Colab](#executar-no-google-colab)
6. [Resultados Esperados](#resultados-esperados)
7. [Contribuição](#contribuição)
8. [Licença](#licença)

---

## **Visão Geral**

O projeto foi desenvolvido para ajudar na classificação automatizada de radiografias da coluna vertebral, utilizando técnicas avançadas de aprendizado profundo. O modelo foi treinado com um dataset específico contendo 338 amostras distribuídas entre as três classes mencionadas. A implementação segue boas práticas de machine learning, incluindo data augmentation, regularização e callbacks para otimização do treinamento.

---

## **Requisitos**

Para executar este projeto localmente, você precisará dos seguintes pacotes instalados:

- Python >= 3.8
- Jupyter
- Keras >= 3.0
- TensorFlow >= 2.13 (compatível com Keras moderno)
- KaggleHub
- Matplotlib
- Seaborn
- Scikit-Learn

Instale as dependências necessárias com o seguinte comando:

```bash
pip install kagglehub keras scikit-learn matplotlib seaborn
```

---

## **Estrutura do Projeto**

O projeto está organizado da seguinte forma:

```
.
├── README.md                  # Documentação do projeto
├── train.ipynb                # Notebook principal para treinamento do modelo
└── modelo_coluna_final.keras  # Modelo treinado salvo no formato .keras
```

---

## **Como Usar**

### **Treinamento do Modelo**

1. **Download do Dataset**:
   - O dataset utilizado está disponível no Kaggle Hub. Para baixá-lo, execute a célula correspondente no notebook `train.ipynb`. Certifique-se de que a biblioteca `kagglehub` está instalada.

2. **Executar o Notebook**:
   - Abra o arquivo `train.ipynb` no Google Colab ou em seu ambiente local.
   - Siga as instruções no notebook para treinar o modelo em duas fases:
     - **Fase 1**: Feature extraction com o backbone congelado.
     - **Fase 2**: Fine-tuning com as últimas camadas do backbone descongeladas.

3. **Salvar o Modelo**:
   - Após o treinamento, o modelo será salvo no formato `.keras` no diretório atual. Você pode baixá-lo diretamente do ambiente de execução.

### **Inferência com Imagens**

1. **Carregar o Modelo Treinado**:
   - Use o script `inference.py` ou o notebook `train.ipynb` para carregar o modelo salvo (`modelo_coluna_final.keras`).

2. **Realizar Inferência**:
   - Execute a função `prever_imagem(caminho_imagem)` fornecendo o caminho de uma imagem de entrada. A função retornará a classe prevista e as probabilidades associadas.

Exemplo de uso no notebook:
```python
from google.colab import files
uploaded = files.upload()

for filename in uploaded.keys():
    predicao_classe, probabilidades = prever_imagem(filename)
    print(f"Imagem: {filename}")
    print(f"Predição: {predicao_classe}")
    print(f"Probabilidades: {probabilidades}")
```

---

## **Executar no Google Colab**

Você pode executar este projeto diretamente no Google Colab sem precisar configurar o ambiente localmente. Acesse o notebook no link abaixo:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1rHAHlBOYvd5wngeP3t69KeHVY6TNjQgi?usp=sharing)

O notebook já está configurado com todas as dependências necessárias e pronto para uso.

---

## **Resultados Esperados**

Após o treinamento, o modelo deve alcançar métricas satisfatórias, incluindo:

- **Acurácia**: Acima de 85% no conjunto de validação.
- **Matriz de Confusão**: Visualização detalhada das previsões por classe.
- **Relatório de Classificação**: Precision, Recall e F1-Score para cada classe.

Os resultados podem variar dependendo das configurações de treinamento e do hardware utilizado.

---

## **Contribuição**

Contribuições são bem-vindas! Se você deseja melhorar este projeto, siga os passos abaixo:

1. Faça um fork deste repositório.
2. Crie uma branch com sua modificação: `git checkout -b feature/nome-da-feature`.
3. Envie suas alterações: `git push origin feature/nome-da-feature`.
4. Abra um pull request explicando suas modificações.

---

## **Contato**

Para dúvidas ou sugestões, abra uma issue neste repositório ou entre em contato diretamente com o mantenedor.