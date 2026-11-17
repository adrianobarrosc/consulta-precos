# Consulta de Preços Públicos

Ferramenta web para pesquisa de preços em **atas de registro de preços vigentes** publicadas no
[PNCP — Portal Nacional de Contratações Públicas](https://pncp.gov.br).

**Acesse:** https://adrianobarrosc.github.io/consulta-precos/

## O que faz

- Busca o item (ex.: `pneu 195/65 R15`) nas atas vigentes de todo o país, com filtros de UF, esfera, adesão e órgão (CNPJ).
- Abre os itens de cada ata e traz o **valor unitário registrado**, o valor estimado, o fornecedor e a vigência.
- Calcula **mediana, média, mínimo e máximo**, com gráfico de distribuição. As amostras podem ser marcadas ou desmarcadas.
- Avisa quando há unidades de medida diferentes e valores muito distantes da mediana.
- Oculta por padrão os lances de cadastro reserva (2º colocado em diante).
- Exporta um relatório em CSV e copia um resumo pronto para o processo.

## Como funciona

É uma página estática, em um único arquivo (`index.html`), sem servidor e sem banco de dados.
As consultas vão direto do navegador para as APIs públicas do PNCP:

- `GET /api/search/` — localiza as atas pelo objeto (busca do portal PNCP);
- `GET /api/consulta/v1/atas` — atas por período de vigência e órgão (API de Consulta);
- `GET /api/pncp/v1/orgaos/{cnpj}/compras/{ano}/{seq}/itens` e `.../itens/{n}/resultados` — itens e valores homologados.

## Base legal

Pesquisa de preços com base em contratações similares da Administração Pública, inclusive por
sistema de registro de preços (Lei nº 14.133/2021, art. 23, §1º, II). Revise unidades de medida e
valores atípicos antes de adotar a mediana como referência.

## Atualizar

Substitua o `index.html` por uma nova versão. O GitHub Pages republica o site automaticamente em cerca de 1 minuto.
