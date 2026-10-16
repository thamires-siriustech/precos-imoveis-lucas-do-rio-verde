# Quanto custa morar em Lucas do Rio Verde (MT): o mercado imobiliário por dentro

Análise de dados que mede quanto custa comprar um imóvel em Lucas do Rio Verde hoje, como o preço por m² varia entre os bairros e como a cidade se compara à capital do estado — a partir de um dataset de anúncios construído a partir dos sites das imobiliárias locais.

> **Pergunta de negócio:** Quanto custa morar em Lucas do Rio Verde hoje, como o preço varia entre bairros, e como se compara ao de uma capital?

---

## Este é o 3º projeto de uma análise em três camadas

- **[Camada 1 — Projeção populacional e demanda habitacional](https://github.com/thamires-siriustech/previsao-populacional-lucas-do-rio-verde)** estima a demanda bruta total de moradias entre 2027 e 2035 a partir do crescimento populacional.
- **[Camada 2 — Oferta habitacional](https://github.com/thamires-siriustech/habitacao-social-lucas-do-rio-verde)** mediu a *oferta* real de habitação de interesse social e o descompasso com a demanda.
- **Camada 3 (este repositório)** mede o *preço*: quanto custa o imóvel em Lucas hoje, e onde.
- **[Camada 4 — Acessibilidade](https://github.com/thamires-siriustech/acessibilidade-imovel-lucas-do-rio-verde)** compara esses preços com faixas de renda e simula cenários de financiamento.

A sequência conecta crescimento populacional, oferta social, preços anunciados e acessibilidade. Ela organiza hipóteses para investigar, mas não prova causalidade entre as quatro dimensões.

## Principais resultados

- O m² residencial em Lucas gira em torno de **R$ 6.212 (mediana)**, com a metade central dos anúncios típicos entre ~R$ 4.570 e R$ 7.478/m².
- **Uma cidade do interior cobra ~90% do m² da capital:** Lucas fica a apenas ~10% abaixo de Cuiabá (FipeZap), que tem quase sete vezes a sua população — o achado central do projeto.
- **Geografia de preços marcada:** do Parque das Emas e Bandeirantes (~R$ 7.700 a 8.000/m²) ao Jardim Imperial e Jardim Primavera (~R$ 3.600 a 4.200/m²) — a diferença entre as médias dos extremos é de cerca de **119%**, em relação ao bairro mais barato.
- **Apartamento custa ~46% mais por m² que casa** (medianas de R$ 7.624 vs R$ 5.217).
- O imóvel típico sai por volta de **R$ 540 mil**, com a entrada no mercado perto de **R$ 205 mil**.

## Metodologia

1. **Construção do dataset** — não existe índice público de preço para Lucas (o FipeZap cobre só grandes cidades; em MT, apenas Cuiabá). O dataset foi coletado dos sites de **13 imobiliárias e portais locais**, com preço, área construída e bairro de cada imóvel: **233 anúncios de 25 bairros**, após remoção de três linhas exatamente duplicadas.
2. **Critério de qualidade** — o preço/m² só é calculado sobre **área construída**. Fontes que só informavam área de terreno foram descartadas; de uma fonte cujos cards misturavam construída e terreno nas casas, entraram apenas os apartamentos.
3. **Separação do mercado típico** — imóveis atípicos (mansões de luxo, micro-investimento) são marcados e separados; a análise principal usa os **186 típicos**.
4. **Análise** — distribuição do preço/m², mapa de preços por bairro (bairros com 5+ anúncios), casa × apartamento e faixa de orçamento, e comparação regional com Cuiabá e Brasil (FipeZap).

## Stack técnico

- **Python** — pandas, numpy
- **Visualização** — matplotlib
- **Coleta** — extração assistida por navegador dos sites das imobiliárias
- **Ambiente** — Jupyter Notebook

## Como executar

```bash
git clone https://github.com/thamires-siriustech/precos-imoveis-lucas-do-rio-verde.git
cd precos-imoveis-lucas-do-rio-verde
pip install -r requirements.txt
jupyter notebook analise_precos_lucas_do_rio_verde.ipynb
```

Mantenha o notebook e o CSV na mesma pasta. No Jupyter, use **Kernel → Restart & Run All**.

## Estrutura do repositório

```
precos-imoveis-lucas-do-rio-verde/
├── analise_precos_lucas_do_rio_verde.ipynb   # análise completa
├── precos_imoveis_lucas.csv                  # dataset de anúncios (233 registros)
├── requirements.txt
└── README.md
```

## Limitações

- **Retrato do momento (outubro/2026), não série histórica** — anúncios antigos não ficam arquivados.
- **Preço de anúncio, não de fechamento** — valor pedido, geralmente acima do preço real de venda.
- **Possível sobreposição entre fontes** — imobiliárias de Lucas trabalham com carteira aberta; a verificação por área+preço não encontrou duplicatas óbvias, mas o risco não é zero.
- **Áreas vêm do próprio anúncio**, não de medição independente.
- **Comparação regional com fontes distintas** — Lucas vem de anúncios; Cuiabá e Brasil, do FipeZap. Indica ordem de grandeza, não medição idêntica.

## Fonte dos dados

Anúncios de venda coletados dos sites de 13 imobiliárias e portais de Lucas do Rio Verde (Domus, MGF, Nossa Casa, Agro+, Benedetti, Volpato, Tati Griebler, Viva, Dinâmica, Modelo, Ideal, ZAP e Loft). Índice FipeZap (abril/2026) como referência regional de Cuiabá e Brasil.

---

**Autora:** Thamires Martins da Silva
Projeto de portfólio em análise de dados — Camada 3 de 4.
