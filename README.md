# Política de Privacidade — SyncView

Última atualização: 07/09/2026

## O que o SyncView faz

O SyncView é um aplicativo de desktop para Windows que permite compartilhar a
tela do seu computador através de um link, usando conexão direta (P2P) via
WebRTC. Quem assiste abre o link em um navegador — não precisa instalar nada.

## Quais dados o SyncView coleta

**Nenhum.** O SyncView não coleta, armazena nem envia para nenhum servidor:

- vídeo ou áudio da sua transmissão;
- informações pessoais (nome, e-mail, localização, contatos);
- histórico de uso ou telemetria;
- arquivos do seu computador.

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

O SyncView usa o **Cloudflare Tunnel** (`cloudflared`) para expor o link de
transmissão fora da rede local. O uso desse serviço está sujeito à própria
política de privacidade da Cloudflare, disponível em
https://www.cloudflare.com/privacypolicy/. O SyncView não compartilha dados
pessoais com a Cloudflare além do necessário para o funcionamento técnico do
túnel.

## Contato

Dúvidas sobre esta política podem ser enviadas para: luizbiel222@gmail.com
