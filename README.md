# 🛒 Analisador de Preços Pro (Python)

Uma ferramenta interactiva via terminal desenvolvida para facilitar a gestão e análise rápida de dados de inventário. Este script permite o registo dinâmico de produtos e gera métricas automáticas sobre os valores inseridos.

## 📖 Sobre o Projeto
Este projeto foi criado para resolver a necessidade de uma análise instantânea de preços durante a entrada de dados. Utiliza estruturas fundamentais do Python, como listas de armazenamento dinâmico e laços de repetição com validação de dados.

## 🌟 Funcionalidades Principais
* ✅ **Contagem Total:** Monitorização exata da quantidade de itens registados.
* 📊 **Média de Mercado:** Cálculo automático do valor médio dos produtos.
* 🔝 **Destaques de Preço:** Identificação do(s) produto(s) de maior e menor valor.
* 💰 **Filtro Premium:** Contagem de itens acima de R$ 1.000,00.

## 🛠️ Tecnologias
* **Python 3.x**
* Biblioteca `time`
* Funções `sum()`, `max()` e `min()`

## 💻 Código Fonte

```python
from time import sleep

# Inicialização das estruturas de dados
produtos = list()
precos = list()
continuar = 'S'
c = c1 = 0
media = 0.0

print("-" * 30)
print("  ANALISADOR DE PREÇOS PRO  ")
print("-" * 30)

# Estrutura principal de recolha de dados
while True:
    produtos.append(str(input('Digite o nome do produto: ')))
    precos.append(float(input('Digite o preço do produto: ')))
    
    # Validação da resposta de continuidade
    continuar = str(input('Deseja continuar? [S/N] ')).upper().strip()[0]
    while continuar not in 'SN':
        continuar = str(input('Resposta inválida. Digite novamente [S/N]: ')).upper().strip()[0]
    
    print("-" * 20)
    c += 1
    
    if continuar == 'N':
        print('\nEncerrando o sistema...')
        sleep(1)
        print('✅ PROGRAMA ENCERRADO COM SUCESSO!')
        break

# Processamento e Exibição dos Resultados
if len(precos) > 0:
    media = sum(precos) / len(precos)
    
    print("\n" + "="*40)
    print(f"📊 RELATÓRIO FINAL DE ANÁLISE")
    print("="*40)
    print(f"✔️ Total de produtos: {c}")
    print(f"✔️ Média dos preços: R$ {media:.2f}")

    # Identificação dos produtos extremos
    produtoMaisCaro = max(precos)
    print(f"✔️ Produto(s) mais caro(s) (R$ {produtoMaisCaro:.2f}): ", end='')
    for i in range(len(precos)):
        if precos[i] == produtoMaisCaro:
            print(f"[{produtos[i]}] ", end='')

    produtoMaisBarato = min(precos)
    print(f"\n✔️ Produto(s) mais barato(s) (R$ {produtoMaisBarato:.2f}): ", end='')
    for i in range(len(precos)):
        if precos[i] == produtoMaisBarato:
            print(f"[{produtos[i]}] ", end='')

    # Filtro de produtos acima de R$ 1000
    for preco in precos:
        if preco > 1000.00:
            c1 += 1
    print(f'\n✔️ Produtos acima de R$ 1.000,00: {c1}')
    print("="*40)
