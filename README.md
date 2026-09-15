# Funil LP — vídeo + triagem

Landing page estática independente para testar um funil minimalista de licenciamento iGreen. Não depende da LP principal para funcionar; logo e favicon são cópias locais.

## Jornada

1. Vídeo em destaque. O botão de entrada fica acessível no cabeçalho fixo e aparece novamente depois do vídeo.
2. Ao entrar na análise, a apresentação sai de cena instantaneamente.
3. Nome, e-mail, WhatsApp, objetivo, experiência em vendas e disponibilidade aparecem um por vez, sem contador de passos. As escolhas de perfil avançam após a seleção; é possível voltar e editar.
4. O resultado substitui o quiz e mostra atendimento por WhatsApp e auto conexão com peso visual igual até o visitante passar o mouse ou usar o foco do teclado.

O questionário abre ao clicar em **Descobrir meu perfil**. O vídeo é um convite, sem bloqueio obrigatório: isso evita prender o visitante quando o player externo falha e permite comparar visualizações com conclusão do questionário. A classificação é apenas uma orientação de comunicação, não uma promessa de renda nem uma decisão de elegibilidade.

## Vídeo

A mídia inicial é o vídeo institucional 2026 usado na LP principal (`qdeblguZdGc`). Ele serve para testar a interface, mas o teste do funil deve receber uma apresentação própria de **8 a 12 minutos** antes de receber tráfego. Substitua `videoId` no início de `script.js`; o script sincroniza o iframe. Revise o título acessível do iframe. A página não incorpora o vídeo do site do colega.

Sugestão de roteiro para a gravação:

- 0:00–0:45 — pergunta forte sobre trabalhar com mercados essenciais; dizer para quem é a apresentação e o que a pessoa entenderá até o fim.
- 0:45–2:30 — apresentar a iGreen e as frentes de energia, telecom e outras soluções, sem estatísticas ou ganhos não verificados.
- 2:30–5:00 — mostrar o papel comercial do licenciado com um exemplo concreto: encontrar um cliente, entender a necessidade, conectar a solução e acompanhar a carteira.
- 5:00–7:30 — mostrar plataforma, suporte e treinamento; responder às dúvidas de quem está começando.
- 7:30–9:30 — explicar que é licenciamento empresarial, que há condições comerciais e que ganhos dependem de atuação e regras vigentes.
- 9:30–10:30 — convidar a pessoa a responder a triagem e escolher entre conversar com o time ou continuar por conta própria.

Abrir cada bloco com uma dúvida que o próximo responde ajuda a manter atenção sem prometer um resultado. A duração e as informações comerciais devem ser conferidas na versão final antes de colocar tráfego.

## Integrações

`CONFIG`, no começo de `script.js`, contém o destino de auto conexão, o WhatsApp e o endpoint já utilizado no projeto principal. O payload conserva `site_id: "rendaverde-igreen"` e usa `landing_page_id: "teste-lp-video-quiz"`, além de `page_url` e UTMs, para distinguir esta experiência. O lead é transmitido quando a pessoa conclui a triagem com autorização de contato. Pré-visualizações em `localhost`, `127.0.0.1` e `file:` não transmitem leads. Um Beacon aceito ou POST opaco indica tentativa de transmissão, não confirmação de gravação na planilha. Verifique a recepção real em uma rodada controlada antes de publicar.

Os mesmos IDs públicos de Google Analytics e Microsoft Clarity estão configurados para comparação com a LP principal. Os campos do formulário usam `data-clarity-mask`.

## Validação

Abra `index.html` em um servidor estático local para testar o iframe, o formulário e os links. Execute `node --check script.js`. Em desktop e mobile, confira a presença do botão no cabeçalho durante o vídeo, a substituição instantânea das telas, cada pergunta isolada, avanço/retorno, máscara e validação do WhatsApp, consentimento, perfis e os destinos finais. Uma submissão real envia um lead ao endpoint configurado; use dados de teste identificáveis.
