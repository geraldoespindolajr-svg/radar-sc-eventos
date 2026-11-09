# Radar SC — contrato de pesquisa e publicação

Projeto **independente** de Marco Zero e de projetos da ZapSign. O design usa cores e tipografia inspiradas no guia de marca, sem logotipo oficial.

Atualização do contrato em 08/11/2026: periodicidade quinzenal e critérios de pesquisa aprofundada. A agenda publicada não é alterada apenas pela mudança de periodicidade.

## Arquivos e publicação
- `index.html`: central única de fontes e locais, gerada de `fontes.json`. Em 09/11/2026: 162 fontes e 113 locais físicos vinculados. Consultar os totais atuais, sem fixá-los na tarefa.
- `fontes.json`: fonte de consulta e ampliação do inventário. Chaves: `metadados`, `fontes`. Cada fonte tem `id`, `cidade`, `nome`, `tipo`, `subtipo`, `temas`, `url`, `agenda_url`, `situacao`, `observacao` e `prioridade`.
- `eventos.html`: agenda visual, lê `eventos.json`.
- `eventos.json`: dados publicados dos eventos.
- Hospedagem: https://radar-sc-eventos.onrender.com
- Repositório: https://github.com/geraldoespindolajr-svg/radar-sc-eventos
- Render: Static Site `srv-dbobshk9v7es73erakvg`, workspace `tea-dbn40c8n74is73eiiung`.

**Atenção:** o Render foi criado com URL pública do GitHub, não com uma instalação do Git provider. O commit isolado pode não gerar deploy automático. Após atualizar `eventos.json`, verificar se já há deploy do commit; na ausência de deploy automático em curso ou concluído para esse commit, acionar explicitamente `Render.trigger_deploy` e conferir o status `live` e o commit. Não gerar deploy duplicado. Em 08/11/2026, commit -> deploy API -> live foi testado. Não dizer que a página foi atualizada se a nova publicação não puder ser confirmada.

## Escopo
Cidades exclusivamente: Balneário Camboriú, Itajaí, Blumenau, Joinville e Florianópolis (SC).
Temas: desenvolvimento pessoal, profissional, negócios, comunicação, oratória, vendas consultivas/enterprise, negociação, liderança, IA, tecnologia, empreendedorismo, saúde/bem-estar educacional, finanças, gestão, carreira, produtividade, autoconhecimento, inteligência emocional, networking e criatividade.
Formatos: cursos, palestras, workshops, imersões, masterclasses, mentorias coletivas, meetups, conferências, congressos, feiras profissionais, capacitações e rodadas de negócio. Pagos, gratuitos e preço não informado. Presencial e híbrido; confirmar local da parte presencial.
Relevância determina os destaques, não um limite artificial ao inventário. Não preencher com festas e entretenimento sem componente de desenvolvimento.

## Frequência e janelas
**A cada duas semanas, em segundas-feiras alternadas, às 07h, America/Sao_Paulo.**
Próxima execução após o teste de 08/11/2026: **23/11/2026**. Depois: 07/12/2026, 21/12/2026 e assim por diante, em intervalos de 14 dias. O agendamento anterior de 09/11/2026 foi substituído.

- Próximos 0–14 dias: máxima atenção a oportunidades imediatas, inscrições e prazos anteriores à próxima execução.
- Dias 15–30: pesquisa detalhada para planejamento.
- Dias 31–90: programas e oportunidades futuras.
- Dias 91–180: congressos, cursos e imersões que exigem antecedência.
- Pesquisar anúncios desde a última pesquisa efetivamente publicada, com dois dias de sobreposição. Sem histórico disponível, pesquisar pelo menos os últimos 16 dias. Em caso de falha de uma rodada, ampliar a janela desde a última execução bem-sucedida.
- Não excluir eventos futuros apenas por terem sido anunciados antes dessa janela.
- Destacar encerramento de inscrições e mudança de lote antes da próxima execução, mesmo para eventos distantes.

Cada cidade recebe pesquisas próprias, inclusive entidades pequenas. Usar `fontes.json` como ponto de partida, mas buscar fontes novas. Dar preferência a `agenda_url` de fontes com `prioridade` Principal. Hotéis são termos de busca, não prova de agenda.
**Não há monitoramento nos dias intermediários.** Uma pesquisa aprofundada não garante capturar um evento anunciado e encerrado entre duas execuções.

## Pesquisa cirúrgica: procedimento de cobertura
1. Carregar a base atual inteira e tentar consultar individualmente as fontes cadastradas. Priorizar agendas diretas, organizadores e páginas de inscrição, sem encerrar a pesquisa após encontrar dez eventos.
2. Registrar por fonte: ID/nome, URL efetivamente consultada, data, resultado e situação: `consultada_com_eventos`, `consultada_sem_eventos_elegiveis`, `acesso_limitado`, `sem_agenda_publica` ou `nao_consultada`.
3. Ler o cadastro ou tentar abrir uma URL não equivale a verificar a agenda. Só contar como consultada uma fonte cujo conteúdo relevante tenha sido efetivamente lido. Diferenciar tentativa de acesso de consulta efetiva.
4. Quando houver falha, tentar até duas rotas alternativas pertinentes, como página oficial específica e busca por nome/local. Persistindo o bloqueio, registrar a limitação e continuar, sem preencher lacunas por suposição.
5. Se não for possível cobrir toda a base, declarar cobertura parcial e listar fontes pendentes e prioridades. Não afirmar busca exaustiva nem inflar as contagens.
6. Pesquisar as cinco cidades separadamente. Não concentrar toda a investigação nas cidades de maior divulgação.

### Centros de eventos, salas e espaços
Considerar centros de convenções, hotéis, salas de treinamento, auditórios, universidades, associações, coworkings, hubs, centros de inovação, escolas e espaços independentes.
Para local sem agenda pública, cruzar seu nome e cidade com eventos, cursos, palestras, workshops, networking e datas futuras em páginas de organizadores, Sympla, Even3, Doity, Eventbrite, Meetup e divulgações públicas acessíveis.
Um site de locação confirma a existência do espaço, não sua programação. Usar diretórios de Convention Bureaux e os locais dos eventos encontrados para descobrir lacunas. Registrar novas fontes com evidência, distinguindo organizador, local e patrocinador.
**O cadastro não é um censo de todos os espaços e salas das cidades.** Novas fontes devem constar como propostas de inclusão no relatório, sem alterar automaticamente o catálogo ou seu HTML.

## Critérios
- Verificar cada evento em página atual do organizador, plataforma de ingresso ou fonte confiável. Preferir página oficial e inscrição; cruzá-las quando disponíveis ou diante de divergência. Não copiar eventos de anos anteriores.
- Não inventar datas, horários, preço, ingressos, disponibilidade, reputação ou links.
- Sem preço divulgado: `price_type=nao_informado`, sem `price` inventado.
- Grátis só quando a gratuidade estiver confirmada: `price_type=gratis`. Pagos confirmados: `price_type=pago`.
- Se só houver data, registrar `start` em YYYY-MM-DD, sem inventar horário. Conservar a data de término quando disponível e manter eventos de vários dias até o encerramento.
- Conferir cidade/endereço da atividade presencial, público, restrições de associados/convidados/seleção e prazos de inscrição.
- Anúncios sem data confirmada e conflitos não resolvidos ficam em pendências/notas, fora da agenda confirmada.
- Deduplicar por edição, URL, nome, cidade e data. Preservar IDs estáveis.
- Comparar com `eventos.json` anterior, conservar eventos futuros válidos enquanto não houver notícia de cancelamento ou adiamento. Retirar já ocorridos da agenda ativa. Não substituir dados confiáveis por informação não confirmada.
- Não apagar um evento apenas porque não reapareceu nas buscas. Se não puder ser revalidado, conservar a data real anterior de verificação e sinalizar essa condição. Não simular nova verificação.
- Atualizar datas, locais, preços, cancelamentos, adiamentos, esgotamentos e encerramentos com evidência. Não sobrescrever toda a agenda com uma amostra menor nem apagar histórico sem necessidade.
- Nunca inferir que ausência de resultado = ausência de evento.
- Registrar cobertura e limitações. A meta é abrangência verificável, não alegação de totalidade.

## Esquema de eventos.json
```json
{
  "version": 1,
  "updated_at": "ISO-8601 timestamp",
  "timezone": "America/Sao_Paulo",
  "scope": "quinzenal",
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
Preservar os campos existentes pertinentes, incluindo término, ressalvas e restrições. Ampliar `coverage` com registros por fonte, fontes sem agenda e fontes não consultadas, distinguindo tentativa e consulta efetiva. Nunca modificar o frontend apenas para mudar a periodicidade.
`scope=piloto` significa pesquisa inicial parcial, **não** varredura completa. Novas execuções regulares usam `scope=quinzenal`; registros históricos mantêm sua classificação original.

## Atualização em GitHub e Render
1. Consultar `fontes.json` e `eventos.json` no repositório principal.
2. Pesquisar as fontes públicas na web. Não afirmar cobertura de fontes não acessadas.
3. Preparar `eventos.json` válido com dados verificados e comparar com registros anteriores. Usar `updated_at` real e `scope=quinzenal`.
4. Usar conector GitHub: `fetch_file` de `eventos.json` para obter blob SHA atual e `update_file` com JSON completo e esse SHA, na branch `main`.
5. Após commit confirmado, verificar os deploys do serviço `srv-dbobshk9v7es73erakvg`, workspace `tea-dbn40c8n74is73eiiung`. Se não houver deploy automático em curso ou concluído do commit atualizado, chamar `Render.trigger_deploy`. Confirmar `live` com commit correto e, quando acessível, o conteúdo de `eventos.json` público.
6. Se alguma etapa falhar, **não declarar publicação bem-sucedida**. Preservar os dados e entregar o relatório no ChatGPT com a falha e o status real do site.
7. A rotina altera os dados de eventos. Não modificar HTML, código, `fontes.json`, outros projetos ou infraestrutura sem autorização adicional.

## Relatório da tarefa
Entregar até dez oportunidades personalizadas com justificativa concreta, agenda elegível completa no site por cidade e horizonte, gratuitos/pagos/preço não informado, networking, mudanças desde a pesquisa anterior, inscrições e prazos anteriores à próxima rodada, pendências e auditoria de cobertura. Links diretos e datas reais; nenhum evento sem fonte.
Informar separadamente fontes verificadas, sem agenda, inacessíveis e não consultadas, e o status real de publicação.
Página de resultados: https://radar-sc-eventos.onrender.com/eventos.html

Na primeira execução de cada mês, além da consulta de eventos, reforçar a descoberta de novas fontes e propor inclusões no cadastro. Nas demais, registrar descobertas sem reconstruir o mapeamento do zero. Não sobrescrever `fontes.json` nem `index.html` automaticamente sem preservar os registros e a estrutura.


## Central única — consolidação autorizada em 09/11/2026

O cadastro canônico continua sendo `fontes.json`, na chave `fontes`. Foram preservados todos os 101 IDs SC e campos anteriores, acrescentadas 61 fontes e vinculados os 113 locais do mapeamento físico. Não somar fontes e locais: são métricas diferentes. Os locais já associados a uma fonte foram incorporados a essa ficha, sem duplicar instituições.

Cada fonte pode conter `locais_fisicos`, uma lista de unidades com ID `LOCAL-xxx`, nome, cidade, tipo, ambientes/salas, endereço informado, `fonte_url`, `agenda_url`, evidência, data documental, observações e `rota_consulta`. `fonte_id` identifica a ficha SC correspondente. `papeis` permite que uma instituição seja simultaneamente organizadora e local, preservando o `tipo` principal anterior.

Na consulta de fontes, percorrer também TODAS as unidades em `locais_fisicos`, mesmo que o tipo principal seja Organizador ou a cidade da fonte seja Fontes compartilhadas. Consultar os links da unidade e cruzar seu nome, ambientes e cidade com divulgações dos organizadores. Páginas de locação não confirmam agenda futura. Não registrar unidade como consultada apenas por ler seu cadastro. As mesmas regras de rastreabilidade, acesso, restrições e validação de eventos continuam valendo.

O catálogo público oferece filtros por cidade/unidade, função da fonte, canal de consulta e tipo de espaço, incluindo busca por nomes de salas. As unidades físicas de fontes compartilhadas aparecem ao filtrar a cidade correspondente. O JSON exportado pela página corresponde ao cadastro canônico nesta publicação. Em futuras atualizações autorizadas da base, manter `index.html` e `fontes.json` consistentes no mesmo commit, sem editar uma cópia independente de locais.

Esta consolidação alterou somente fontes, apresentação do catálogo e sua documentação. Não ampliou temas, não modificou eventos nem reconfigurou a periodicidade quinzenal. O mapeamento não equivale a censo de todos os espaços das cidades, agenda auditada, disponibilidade de locação ou endosso dos serviços.
