# Alocação de Famílias de Baixa Renda a Agências Bancárias

Projeto acadêmico de **Pesquisa Operacional** que aplica um modelo de **programação linear inteira mista (MILP)** para alocar famílias de baixa renda a agências bancárias, equilibrando **eficiência** (minimização do deslocamento) e **equidade espacial** (distribuição balanceada entre agências, evitando sobrecarga ou ociosidade).

## 📌 Sobre o projeto

Este problema é especialmente relevante em grandes centros urbanos, onde a desigualdade no acesso a equipamentos públicos é um desafio recorrente. Um caso de aplicação direta é a gestão de programas sociais como o Bolsa Família e o Cadastro Único, nos quais famílias precisam ser designadas a pontos de atendimento de forma organizada e justa.

A abordagem é generalizável para outros contextos de planejamento territorial, como:
- alocação de estudantes a escolas públicas;
- distribuição de pacientes a unidades de saúde;
- designação de famílias a CRAS/CREAS;
- planejamento logístico de postos de vacinação, agências móveis e centros de coleta de alimentos.

O modelo tem relevância tanto **operacional** — reduzindo custos e deslocamentos — quanto **social**, ao promover um atendimento mais equitativo em regiões de maior vulnerabilidade socioeconômica.

## 🧮 Modelagem matemática

O problema é formulado como um **MILP**, cuja função objetivo busca um tradeoff entre:
- **Eficiência**: minimizar a distância total entre famílias e agências;
- **Equidade**: penalizar agências que fiquem muito acima ou abaixo da alocação média ideal de famílias.

O peso desse tradeoff é controlado por um parâmetro de penalização, permitindo analisar diferentes cenários de sensibilidade (ex: variação dos pesos da função objetivo e da capacidade máxima das agências).

## 🛠️ Tecnologias e ferramentas

- **Python 3**
- [**Gurobi**](https://www.gurobi.com/) (`gurobipy`) — solver de otimização utilizado para resolver as instâncias do modelo
- **NumPy** — geração e manipulação de dados
- **Matplotlib** — visualização da evolução dos limites (upper/lower bound) durante a otimização

## 📂 Estrutura do notebook

O notebook (`ProjetoIPO_Grupo2.ipynb`) está organizado nas seguintes seções:

1. **Introdução** — contextualização do problema
2. **Modelagem Matemática** — formulação do modelo MILP
3. **Instalação das Ferramentas** — setup do ambiente (Gurobi)
4. **Implementação do modelo** — construção do modelo no Gurobi
5. **Cálculo das distâncias** — geração da matriz de distâncias entre famílias e agências
6. **Geração de Instâncias** — criação de instâncias de teste de diferentes tamanhos
7. **Leitura das instâncias**
8. **Análise de Resultados**
9. **Execução do Projeto**
10. **Discussão dos Resultados Obtidos**
11. **Função de Callback** — acompanhamento da evolução dos limites (bounds) durante a resolução
12. **Execuções com callback** (instâncias 3 e 4)
13. **Discussões Finais e Conclusão**

## ▶️ Como executar

Este projeto foi desenvolvido no Google Colab e requer uma licença do Gurobi (acadêmica ou trial) para rodar instâncias maiores.

1. Abra o notebook `ProjetoIPO_Grupo2.ipynb` no [Google Colab](https://colab.research.google.com/) ou no Jupyter local.
2. Instale as dependências (a primeira célula já faz isso via `%pip install gurobipy`):
   ```bash
   pip install gurobipy numpy matplotlib
   ```
3. Configure sua licença do Gurobi, caso necessário ([veja como obter uma licença acadêmica](https://www.gurobi.com/academia/academic-program-and-licenses/)).
4. Execute as células em ordem.

> **Nota sobre as instâncias de teste:** os arquivos de instância **não estão incluídos neste repositório**, pois ultrapassam o limite de tamanho de arquivo do GitHub (100 MB). Eles são **gerados automaticamente** pela seção "Geração de Instâncias" do notebook, utilizando uma seed fixa (`np.random.seed` / `random.seed`) — basta executar essa célula para recriar exatamente as mesmas instâncias usadas nos testes originais, garantindo a reprodutibilidade dos resultados.

## 📊 Resultados

O modelo foi testado em instâncias de diferentes tamanhos — desde problemas simples com poucas famílias e agências até problemas de grande escala, com milhares de famílias e centenas de agências. Mesmo nos cenários mais complexos, o modelo produziu soluções eficientes dentro de um tempo limite de execução, evidenciando a viabilidade prática da abordagem para problemas reais de planejamento urbano.
