Parte 1 - Funções em Python e Manipulação de Dados

---

1. Escreva uma função que receba uma lista de números e retorne outra lista com os números ímpares.

# Filtrar números ímpares

def filtrar_impares(lista):
    return [num for num in lista if num % 2 != 0]

# Exemplo
entrada = [1, 2, 3, 4, 5]
# Retorno esperado: [1, 3, 5]


---

2. Escreva uma função que receba uma lista de números e retorne outra lista com os números primos presentes.

# Verifica se o número é primo

def eh_primo(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

# Filtrar primos da lista

def filtrar_primos(lista):
    return [num for num in lista if eh_primo(num)]

# Exemplo: [2, 4, 5, 9, 11] → [2, 5, 11]


---

3. Escreva uma função que receba duas listas e retorne outra lista com os elementos presentes apenas em uma delas.

# Diferença simétrica

def somente_uma(lista1, lista2):
    return list(set(lista1) ^ set(lista2))

# Exemplo: [1, 2, 3] e [3, 4, 5] → [1, 2, 4, 5]


---

4. Dada uma lista de números inteiros, encontre o segundo maior valor.

# Segundo maior valor

def segundo_maior(lista):
    lista_unica = list(set(lista))  # Remove duplicados
    lista_unica.remove(max(lista_unica))
    return max(lista_unica)

# Exemplo: [10, 5, 8, 12, 12] → 10


---

5. Crie uma função que receba uma lista de tuplas (nome, idade) e retorne a lista ordenada pelo nome.

# Ordenar por nome

def ordenar_por_nome(pessoas):
    return sorted(pessoas, key=lambda p: p[0])

# Exemplo
# [("Ana", 20), ("Carlos", 18), ("Beatriz", 25)]


---

Parte 2 — Visualização e Análise de Dados


---

6. Como identificar e tratar outliers usando desvio padrão ou quartis?

Método do Desvio Padrão

media = df['coluna'].mean()
desvio = df['coluna'].std()
lim_inf = media - 3 * desvio
lim_sup = media + 3 * desvio
outliers = df[(df['coluna'] < lim_inf) | (df['coluna'] > lim_sup)]

Método do IQR (Quartis)

Q1 = df['coluna'].quantile(0.25)
Q3 = df['coluna'].quantile(0.75)
IQR = Q3 - Q1
lim_inf = Q1 - 1.5 * IQR
lim_sup = Q3 + 1.5 * IQR
outliers = df[(df['coluna'] < lim_inf) | (df['coluna'] > lim_sup)]

Tratamentos comuns: remover outliers, substituir por mediana, ajustar valores.


---

7. Como concatenar vários DataFrames, mesmo com colunas diferentes?

import pandas as pd

# Empilhar linhas (vertical)
df_total = pd.concat([df1, df2, df3], axis=0)

# Empilhar colunas (horizontal)
df_lado = pd.concat([df1, df2], axis=1)


---

8. Como realizar a leitura de um arquivo CSV e exibir as primeiras linhas?

import pandas as pd

df = pd.read_csv("dados.csv")
df.head()


---

9. Como selecionar uma coluna e filtrar linhas com base em uma condição?

idades = df['idade']
adultos = df[df['idade'] > 30]

# Exemplo com múltiplas condições
# df[(df['idade'] > 20) & (df['salario'] > 3000)]


---

10. Como lidar com valores ausentes (NaN) em um DataFrame?

# Remover NaN
df_limpo = df.dropna()

# Preencher com zero
df_zeros = df.fillna(0)

# Preencher com mediana
df_mediana = df.fillna(df.median())

# Contar valores ausentes
df.isnull().sum()


---
