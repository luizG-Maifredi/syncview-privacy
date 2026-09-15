# Política de Privacidade — SyncView

Última atualização: 15/09/2026

## O que o SyncView faz

O SyncView é um aplicativo de desktop para Windows que permite compartilhar a
tela do seu computador, usando conexão direta (P2P) via WebRTC. Tem dois
modos: **transmissão avulsa** (gera um link; quem assiste abre no navegador,
sem instalar nada) e **sala** (um código curto; quem entra também usa o
SyncView, e qualquer pessoa na sala pode compartilhar a própria tela).

## Quais dados o SyncView coleta

**Nenhum.** O SyncView não coleta, armazena nem envia para nenhum servidor
nosso:

- vídeo ou áudio da sua transmissão;
- informações pessoais (e-mail, localização, contatos);
- histórico de uso ou telemetria;
- arquivos do seu computador.

O único dado pessoal que existe no app é o **nome de exibição** usado nas
salas (opcional — sem ele, você aparece como "Convidado"). Ele fica salvo
apenas no seu computador (`localStorage`, local ao app) e só é enviado
**diretamente para as outras pessoas na mesma sala** (via WebRTC), nunca para
o desenvolvedor do SyncView ou para qualquer servidor nosso.

## Como a transmissão funciona

- O vídeo e o áudio trafegam **diretamente entre quem transmite e quem
  assiste** (conexão WebRTC ponto a ponto). O servidor de sinalização
  embutido no aplicativo só troca metadados técnicos necessários para
  estabelecer essa conexão (ofertas SDP e candidatos ICE) — ele não recebe,
  não processa e não grava o conteúdo da tela ou do áudio transmitido.
- Para permitir que quem assiste acesse o link fora da rede local, o
  aplicativo abre um túnel usando o `cloudflared` (Cloudflare Tunnel). Esse
  túnel roteia a conexão, mas não gera cópia nem log do conteúdo da
  transmissão por parte do SyncView.
- O áudio de aplicativos específicos (quando essa função é usada) é
  capturado localmente do próprio sistema Windows (captura de loopback de
  processo) e enviado apenas para quem está assistindo a transmissão — nunca
  para o desenvolvedor do aplicativo ou terceiros.

## Câmera e microfone

O SyncView **não acessa a câmera nem o microfone** do dispositivo. Ele
compartilha apenas a tela (e, opcionalmente, o áudio que os próprios
aplicativos do Windows estão reproduzindo).

## Permissões do Windows

O aplicativo solicita permissão do Windows para capturar tela (Windows
Graphics Capture) e áudio de aplicativos — permissões exigidas pelo próprio
sistema operacional para essas funções, usadas exclusivamente durante uma
transmissão ativa.

## Serviços de terceiros

- **Cloudflare Tunnel** (`cloudflared`), usado no modo **avulsa** para expor
  o link de transmissão fora da rede local. Sujeito à política de privacidade
  da Cloudflare (https://www.cloudflare.com/privacypolicy/). O SyncView não
  compartilha dados pessoais com a Cloudflare além do necessário para o
  funcionamento técnico do túnel.
- **PeerJS Cloud**, usado no modo **sala** só para o "aperto de mão" inicial
  entre os participantes (trocar os metadados técnicos necessários pra
  estabelecer a conexão direta, usando o código da sala como identificador).
  O conteúdo das mensagens entre participantes (nome, vídeo, áudio) **não
  passa por esse serviço** — ele só existe pra duas pessoas se encontrarem
  antes da conexão P2P ser estabelecida. Sujeito aos termos do projeto PeerJS
  (https://peerjs.com/).

## Contato

Dúvidas sobre esta política podem ser enviadas para: luizbiel222@gmail.com
