# Missão README – Garantia da Qualidade de Software

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Status](https://img.shields.io/badge/Status-Concluído-green)
![Licença](https://img.shields.io/badge/Licença-MIT-yellow)

## Sobre o projeto

Este projeto foi desenvolvido em **Python** com o objetivo de verificar se uma palavra ou frase é um **palíndromo**.

Um **palíndromo** é um texto que pode ser lido da mesma forma da esquerda para a direita e da direita para a esquerda, desconsiderando espaços, pontuação e diferenças entre letras maiúsculas e minúsculas.

Exemplo:

> "Socorram-me, subi no ônibus em Marrocos"

---

## Como executar?

O código pode ser executado utilizando Python instalado no computador ou um ambiente Python online.

Código utilizado:

```python
import re

def analisar(entrada):
    if entrada is None:
        return False

    # Remove tudo que não for letra ou número e converte para minúsculas
    limpa = re.sub(r'[^a-zA-Z0-9]', '', entrada).lower()

    # Inverte a string usando fatiamento (slicing)
    invertida = limpa[::-1]

    return limpa == invertida

if __name__ == "__main__":
    texto1 = "A sacada da casa de cadasa"
    texto2 = "Socorram-me, subi no ônibus em Marrocos"

    print(f"Teste 1: {analisar(texto1)}")
    print(f"Teste 2: {analisar(texto2)}")
```

Ao executar o programa, teremos:

```text
Teste 1: False
Teste 2: True
```

---

# Desvendando os métodos

## O papel do `main`

Em Python, a seguinte estrutura:

```python
if __name__ == "__main__":
```

verifica se o arquivo está sendo executado diretamente.

Quando isso acontece, o programa cria duas variáveis:

```python
texto1 = "A sacada da casa de cadasa"
texto2 = "Socorram-me, subi no ônibus em Marrocos"
```

Depois, cada texto é enviado para a função `analisar()`:

```python
print(f"Teste 1: {analisar(texto1)}")
print(f"Teste 2: {analisar(texto2)}")
```

O resultado retornado pela função é exibido no terminal como `True` ou `False`.

---

## Como funciona `analisar(entrada)`?

A função é responsável por receber o texto, tratá-lo e verificar se ele é um palíndromo.

### 1. Verificação da entrada

```python
if entrada is None:
    return False
```

Primeiro, o programa verifica se foi fornecido algum texto. Caso a entrada seja `None`, a função retorna `False`.

### 2. Limpeza do texto

```python
limpa = re.sub(r'[^a-zA-Z0-9]', '', entrada).lower()
```

O `re.sub()` utiliza uma expressão regular para remover caracteres que não sejam letras ou números.

A expressão:

```text
[^a-zA-Z0-9]
```

identifica caracteres que não pertencem aos intervalos de letras e números definidos.

Depois, `.lower()` transforma as letras em minúsculas para que diferenças entre maiúsculas e minúsculas não interfiram na comparação.

### 3. Inversão

```python
invertida = limpa[::-1]
```

O `[::-1]` é um recurso de **slicing** do Python utilizado para inverter a string.

Assim, o programa consegue comparar o texto normal com sua versão invertida.

### 4. Comparação

```python
return limpa == invertida
```

Por fim, a função compara as duas strings.

* Se forem iguais, retorna `True`.
* Se forem diferentes, retorna `False`.

---

# O Mistério dos Testes

| Teste   | Entrada                                   | Resultado |
| ------- | ----------------------------------------- | --------- |
| Teste 1 | `A sacada da casa de cadasa`              | `False`   |
| Teste 2 | `Socorram-me, subi no ônibus em Marrocos` | `True`    |

## Por que o Teste 1 retorna `False`?

O primeiro texto é:

```text
A sacada da casa de cadasa
```

Depois da remoção dos espaços e conversão para letras minúsculas, o texto não é igual à sua versão invertida.

Por isso, a comparação:

```python
limpa == invertida
```

resulta em `False`.

Isso significa que o **Teste 1 falhou na verificação de palíndromo**, pois a frase não pode ser lida igualmente nos dois sentidos.

## Por que o Teste 2 retorna `True`?

O segundo texto é:

```text
Socorram-me, subi no ônibus em Marrocos
```

Depois do tratamento realizado pelo programa, os caracteres considerados na comparação formam a mesma sequência quando lidos nos dois sentidos.

Por isso:

```python
limpa == invertida
```

resulta em `True`, indicando que o **Teste 2 passou na verificação**.

---

# Recursos utilizados

* Python
* Biblioteca `re`
* Expressões regulares
* Strings
* Slicing
* Estruturas condicionais
* Markdown

---

# Sobre o Autor

Documentação e análise realizadas por **William Lázaro** a partir do fork do repositório disponibilizado para a atividade de **Garantia da Qualidade de Software**.

