# Desafios de Código - Simulando Desafios com IAs Generativas
# 1 / 5 - Analisando Sentimentos

# Descrição

Imagine que você foi designado a criar um algoritmo para analisar o sentimento de um comentário fornecido pelo usuário, simulando análises de sentimentos, um assunto muito comentado dentro do Machine Learning. O programa solicitará ao usuário que insira um comentário e, em seguida, dividirá esse comentário em palavras individuais.

Após isso, ele contará o número de palavras positivas, negativas e neutras dentro do comentário, baseando-se em uma lista pré-definida de palavras-chave. As palavras consideradas positivas incluem "bom", "ótimo", "excelente", "maravilhoso", "gostei" e "incrível" enquanto as palavras negativas incluem "ruim", "péssimo", "horrível", "terrível" e "odeio". Já as palavras neutras incluem "mas", "deixou", "apesar" e "embora".

Depois de calcular as contagens de palavras positivas e negativas, o programa determinará o sentimento predominante do comentário. Se houver mais palavras positivas do que negativas, o sentimento será considerado positivo. Se houver mais palavras negativas do que positivas, o sentimento será considerado negativo. Caso contrário, se houver um número igual de palavras positivas e negativas, o sentimento será neutro.

## Entrada

O usuário será solicitado a fornecer um comentário como entrada para o programa.

## Saída

O programa exibirá o sentimento do comentário inserido pelo usuário, que pode ser "Positivo", "Negativo" ou "Neutro", dependendo da análise das palavras-chave no comentário.

## Exemplos

A tabela abaixo apresenta exemplos com alguns dados de entrada e suas respectivas saídas esperadas. Certifique-se de testar seu programa com esses exemplos e com outros casos possíveis.

| Entrada                                               | Saída              |
|-------------------------------------------------------|--------------------|
| A mentoria foi incrível, aprendi muito!               | Sentimento: Positivo |
| O clima hoje está terrível, odeio dias quentes.       | Sentimento: Negativo |
| A comida estava boa, mas o serviço deixou a desejar. | Sentimento: Neutro   |

## Atenção

Se você não está familiarizado com a linguagem de programação, não se preocupe!
Você pode usar uma das seguintes inteligências artificiais para te ajudar a entender o código:

- ChatGPT: [https://chat.openai.com/](https://chat.openai.com/)
- Copilot: [https://copilot.microsoft.com/](https://copilot.microsoft.com/)
- Gemini: [https://gemini.google.com/](https://gemini.google.com/)
- Amazon Q (Para Empresas): [https://aws.amazon.com/pt/q/](https://aws.amazon.com/pt/q/)

## Abaixo adicionamos algumas sugestões de uso e prompts para te auxiliar na resolução:

| Sugestões de Uso             | Sugestões de Prompts                                                 |
|------------------------------|----------------------------------------------------------------------|
| Explicação de Conceitos      | Pode me explicar o que são estruturas de dados e dar exemplos?       |
| Entendimento do Problema     | Quais são as restrições ou requisitos específicos que devo considerar neste desafio? |
| Sugestões de Abordagem       | Quais são as etapas principais que devo seguir para resolver este desafio? |
| Ajuda na Depuração           | Estou recebendo um erro de sintaxe neste trecho de código. O que pode estar errado? |
| Revisão de Algoritmos        | Você pode revisar meu algoritmo de ordenação e me dar feedback sobre sua eficiência? |


# SOLUÇÃO COMENTADA:

# Explicação do Código

O código abaixo implementa um algoritmo para analisar o sentimento de um comentário fornecido pelo usuário. Ele classifica o comentário como "Positivo", "Negativo" ou "Neutro" com base em listas pré-definidas de palavras positivas, negativas e neutras.

```python

import re
# Este módulo é usado para trabalhar com expressões regulares,
# que permitem realizar buscas e manipulações avançadas em strings.

#analyze_sentiment é uma função que será responsável por analisar o sentimento de um comentário fornecido pelo usuário.
def analyze_sentiment():
    # Entrada do usuário
    comentario = input()

    # Divisão do comentário em palavras
    palavras = re.findall(r'\b\w+\b', comentario.lower())
    # Esta linha utiliza uma expressão regular para encontrar todas as palavras no comentário.
    # O método findall retorna uma lista de todas as ocorrências encontradas.
    # A expressão r'\b\w+\b' significa:
    # \b: Limite de palavra.
    # \w+: Uma ou mais letras ou dígitos.
    # Convertendo o comentário para minúsculas com comentario.lower(), garantimos que a análise seja case-insensitive (não sensível a maiúsculas/minúsculas).
    
    # Lista de palavras positivas, negativas e neutras
    # Estas listas contêm palavras que serão usadas para classificar o sentimento do comentário.
    positivas = ["bom", "boa", "ótimo", "excelente", "maravilhoso", "gostei", "incrível"]
    negativas = ["ruim", "péssimo", "horrível", "terrível", "odeio"]
    neutras = ["mas", "deixou", "apesar", "embora"]

    # Contagem de palavras positivas, negativas e neutras
    # Aqui, contamos quantas palavras da lista palavras estão nas listas positivas e negativas, respectivamente.
    count_positivo = sum(palavra in positivas for palavra in palavras)
    count_negativo = sum(palavra in negativas for palavra in palavras)
    count_neutro = sum(palavra in neutras for palavra in palavras)  # Contagem de palavras neutras

    # Verifica o sentimento com base na contagem de palavras
    if count_positivo > count_negativo and count_neutro == 0:
        return "Positivo"
    elif count_negativo > count_positivo and count_neutro == 0:
        return "Negativo"
    else:
        return "Neutro"

# Saída esperada
# A função analyze_sentiment é chamada e seu resultado é armazenado na variável sentimento, que é então impressa.
sentimento = analyze_sentiment()
print("Sentimento:", sentimento)


