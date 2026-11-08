# Radar SC — contrato de pesquisa e publicação

Projeto **independente** de Marco Zero e de projetos da ZapSign. O design usa cores e tipografia inspiradas no guia de marca, sem logotipo oficial.

## Arquivos e publicação
- `index.html`: catálogo de fontes monitoradas (101 cadastros de referência).
- `fontes.json`: fonte de consulta e ampliação do inventário. Chaves: `metadados`, `fontes`. Cada fonte tem `id`, `cidade`, `nome`, `tipo`, `subtipo`, `temas`, `url`, `agenda_url`, `situacao`, `observacao` e `prioridade`.
- `eventos.html`: agenda visual, lê `eventos.json`.
- `eventos.json`: dados publicados dos eventos.
- Hospedagem: https://radar-sc-eventos.onrender.com
- Repositório: https://github.com/geraldoespindolajr-svg/radar-sc-eventos
- Render: Static Site `srv-dbobshk9v7es73erakvg`, workspace `tea-dbn40c8n74is73eiiung`.

**Atenção:** o Render foi criado com URL pública do GitHub, não com uma instalação do Git provider. O commit isolado pode não gerar deploy automático. Após atualizar `eventos.json`, acionar explicitamente `Render.trigger_deploy` e conferir o status `live` e o commit. Em 08/11/2026, commit -> deploy API -> live foi testado. Não dizer que a página foi atualizada se a nova publicação não puder ser confirmada.

## Escopo
Cidades exclusivamente: Balneário Camboriú, Itajaí, Blumenau, Joinville e Florianópolis (SC).
Temas: desenvolvimento pessoal, profissional, negócios, comunicação, vendas, liderança, IA, tecnologia, empreendedorismo, saúde/bem-estar educacional, finanças, gestão, networking, criatividade.
Formatos: cursos, palestras, workshops, imersões, mentorias coletivas, meetups, conferências, feiras profissionais, capacitações e rodadas de negócio. Pagos, gratuitos e preço não informado. Presencial e híbrido; confirmar local da parte presencial.

## Frequência e janelas
Segunda-feira, 07h, America/Sao_Paulo.
Pesquisar 0-7 e 8-30 dias com profundidade, 31-90 dias para programas futuros e 91-180 dias para congressos/imersões de planejamento antecipado.
Buscar anúncios novos dos últimos 7 dias.
Cada cidade recebe pesquisas próprias, inclusive entidades pequenas. Usar `fontes.json` como ponto de partida, mas buscar fontes novas. Dar preferência a `agenda_url` de fontes com `prioridade` Principal. Hotéis são termos de busca, não prova de agenda.

## Critérios
- Verificar cada evento em página atual do organizador, plataforma de ingresso ou fonte confiável. Preferir página oficial. Não copiar eventos de anos anteriores.
- Não inventar datas, horários, preço, ingressos, disponibilidade ou links.
- Sem preço divulgado: `price_type=nao_informado`, sem `price` inventado.
- Grátis só quando a gratuidade estiver confirmada: `price_type=gratis`. Pagos confirmados: `price_type=pago`.
- Se só houver data, registrar `start` em YYYY-MM-DD, sem inventar horário.
- Deduplicar por URL, nome, cidade e data.
- Comparar com `eventos.json` anterior, conservar eventos futuros válidos enquanto não houver notícia de cancelamento ou adiamento. Retirar já ocorridos. Não substituir dados confiáveis por informação não confirmada.
- Nunca inferir que ausência de resultado = ausência de evento.
- Registrar cobertura e limitações. A meta é abrangência, não alegação de totalidade.

## Esquema de eventos.json
```json
{
  "version": 1,
  "updated_at": "ISO-8601 timestamp",
  "timezone": "America/Sao_Paulo",
  "scope": "semanal",
  "cities": ["Balneário Camboriú","Itajaí","Blumenau","Joinville","Florianópolis"],
  "events": [
    {
      "id": "stable-id",
      "title": "Título",
      "city": "Itajaí",
      "start": "2026-11-10T19:00:00-03:00",
      "category": "Vendas e comunicação",
      "organizer": "Organizador",
      "venue": "Local verificado",
      "description": "Breve descrição factual",
      "price_type": "gratis | pago | nao_informado",
      "price": "Valor confirmado (opcional)",
      "registration_status": "Status verificável ou consultar disponibilidade",
      "source_url": "https://...",
      "registration_url": "https://...",
      "checked_at": "YYYY-MM-DD",
      "format": "presencial | hibrido"
    }
  ],
  "coverage": {"por_cidade": {}, "fontes_consultadas": [], "fontes_nao_acessadas": []},
  "notes": []
}
```
`scope=piloto` significa pesquisa inicial parcial, **não** varredura completa.

## Atualização em GitHub e Render
1. Consultar `fontes.json` e `eventos.json` no repositório principal.
2. Pesquisar as fontes públicas na web. Não afirmar cobertura de fontes não acessadas.
3. Preparar `eventos.json` válido com dados verificados e comparar com registros anteriores.
4. Usar conector GitHub: `fetch_file` de `eventos.json` para obter blob SHA atual e `update_file` com JSON completo e esse SHA, na branch `main`.
5. Após commit confirmado, chamar o conector Render `trigger_deploy` do serviço `srv-dbobshk9v7es73erakvg`, workspace `tea-dbn40c8n74is73eiiung`. Confirmar `live` com commit atualizado.
6. Se alguma etapa falhar, **não declarar publicação bem-sucedida**. Entregar o relatório no ChatGPT com a falha e o status real do site.

## Relatório da tarefa
Entregar Top 10 oportunidades personalizadas, agenda completa verificada por cidade e horizonte, gratuitos/pagos, oportunidades de networking, mudanças desde a semana anterior, prazos e auditoria de cobertura. Links diretos e datas reais; nenhum evento sem fonte.

A cada primeira segunda-feira do mês, além da consulta de eventos, buscar novas fontes e propor inclusões no cadastro. Não sobrescrever `fontes.json` nem `index.html` automaticamente sem preservar os registros e a estrutura.
