# Fluidez.dll, por Gabriel Bitencourt

Deixa o MU Online mais fluido sem recompilar cliente nem servidor: é só colocar dois arquivos na pasta do jogo.

> **Esta é uma versão gratuita e tem algumas limitações.** Para ter a versão paga, entre em contato pelo WhatsApp: [84 99632-9843](https://wa.me/5584996329843).

**Versão atual:** veja o arquivo [VERSAO](VERSAO). O que mudou em cada uma está no [CHANGELOG](CHANGELOG.md).

## O que ela faz

- Sobe o FPS (padrão 120), sem mudar a velocidade do jogo.
- Deixa suave o movimento de personagens, pets e efeitos.
- Dá muito mais FPS em multidão.
- Mantém os efeitos na velocidade original, mesmo com FPS alto.
- Deixa suave o fundo da seleção de servidor com `FpsLimit = 5` (Main fechado do Louis).

Se a DLL não reconhecer alguma parte do seu Main, aquela parte fica como veio.

A DLL não grava nenhum arquivo na pasta do jogo.

## Como instalar

1. Baixe os arquivos da pasta [`dll`](dll): `Fluidez.dll` e `opengl32.dll`.
2. Coloque os dois na pasta do jogo, junto do `Main.exe`.
3. Abra o jogo normalmente.

Para confirmar que está funcionando, crie um `Fluidez.ini` com as linhas `[Fluidez]` e `Contador=1`: o contador de FPS aparece na tela. Depois apague essa opção, porque o contador reduz o desempenho.

**Para desinstalar:** apague `Fluidez.dll`, `opengl32.dll` e, se existir, `Fluidez.ini`.

O `Fluidez.ini` é opcional. Sem ele, a DLL usa os valores padrão, que são os recomendados.

### Se o jogo já tiver um opengl32.dll na pasta

Renomeie o que já existe para `opengl32_original.dll` antes de copiar o novo.

### Main fechado do Louis com a Main.dll antiga

Use `FpsLimit = 5` no `MainInfo`. Com `FpsLimit = 1`, o movimento suave não tem efeito.

**Importante:** um `main.premium` com `FpsLimit = 5` só deve ir para os jogadores junto com esta DLL. Sem ela, efeitos e animações podem ficar acelerados.

## Onde funciona

Medido em i7-13700KF com RTX 3060 Ti.

| Main | Situação | Antes | Com a DLL |
|---|---|---|---|
| ProjectRebirthMu | 400 bots, câmera afastada | 14 FPS (sem a DLL) | 67 FPS |
| Fonte da base do Dinho | 400 bots, câmera afastada | 26 FPS (sem a DLL) | cerca de 95 FPS |
| Louis, com Main.dll antiga | 45 Kunduns na tela | cerca de 35 FPS (v1.0) | 108 a 120 FPS |

Com a Main.dll mais nova do Louis a DLL funciona, mas os ganhos mais recentes ainda não foram medidos nela.

Outro Main fechado fica sem as funções específicas do Louis, sem risco.

## Limitações conhecidas

- Base do Dinho: o brilho da estátua e da fonte de Lorencia estoura em branco com FPS alto. Acontece também sem a DLL, e um limite de FPS menor reduz o efeito.
- Main fechado do Louis em multidão muito grande: os últimos personagens desenhados podem perder parte dos efeitos.
- Corvo do Dark Lord (Dark Spirit) ainda não tem movimento suave no Main fechado.

## Fluidez.ini (opcional)

Crie um arquivo `Fluidez.ini` na pasta do jogo começando com a linha `[Fluidez]`, e coloque só o que quiser mudar.

| Opção | Padrão | O que faz |
|---|---|---|
| `FPS` | 120 | Limite de FPS (0 = sem limite) |
| `VSync` | 0 | 1 liga o VSync |
| `Contador` | 0 | 1 mostra o contador de FPS na tela |
| `Suave` | 1 | 0 desliga o movimento suave |

## Se algo der errado

Apague o `Fluidez.ini`, se tiver, para voltar aos valores padrão. Se o problema continuar, remova a DLL e abra o jogo: se ele acontecer também sem ela, a causa é outra.

## Versões

Cada versão publicada tem uma tag `vX.Y`, e os arquivos dela ficam em **Tags** no GitHub. A partir da v1.2: os arquivos da v1.1 foram retirados.

- **Número da frente (X):** mudança grande, que muda a forma de instalar ou de usar.
- **Número de trás (Y):** correções e melhorias.

A pasta `dll` sempre tem a versão mais recente, e o `SHA256SUMS.txt` traz o hash de cada arquivo para conferir o download.
