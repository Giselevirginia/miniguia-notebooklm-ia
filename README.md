# 📱 Automação de Testes Mobile com Appium em Apps de Streaming

## 🎯 Contexto e Objetivos

Este repositório documenta meu processo de aprendizagem em automação de testes mobile utilizando Appium, com foco na validação de fluxos críticos de aplicações de streaming.

O projeto tem como objetivo simular o comportamento real do usuário e validar a estabilidade da aplicação em cenários comuns, considerando navegação, reprodução de conteúdo e transições de estado do player (play, pause, buffering).

### Objetivos de estudo:

* Compreender a arquitetura e funcionamento do Appium
* Configurar ambiente de automação para Android
* Automatizar fluxos de navegação e reprodução de conteúdo
* Validar estados do player (play, pause, buffering)
* Identificar limitações e desafios da automação mobile

---

## 📚 Curadoria de Fontes

1. Documentação oficial do Appium
   → utilizada para compreender arquitetura, funcionamento do servidor e integração com drivers

2. Guia de automação mobile com Appium
   → base para configuração de ambiente e primeiros testes

3. Artigos sobre testes mobile e flakiness
   → apoio para entendimento de instabilidade em testes e estratégias de mitigação

---

## 🤖 Engenharia de Prompts e Aprendizados

### Prompt 1 (Inicial - Genérico)

Pergunta:
"Explique os conceitos fundamentais para quem quer começar em automação."

Resumo da resposta:
Conteúdo introdutório e amplo, sem foco em mobile ou ferramentas específicas.

Problema identificado:
Baixa aplicabilidade prática.

---

### Prompt 2 (Direcionamento técnico)

Pergunta:
"Como o Appium funciona na prática?"

Resumo da resposta:
Explicação sobre arquitetura do Appium, servidor e interação com drivers.

Aprendizado:
Maior entendimento técnico da ferramenta.

---

### Prompt 3 (Limitações)

Pergunta:
"Quais são as limitações do Appium?"

Resumo da resposta:

* Instabilidade de elementos
* Dependência de ambiente
* Dificuldade em validar conteúdo visual

Insight:
Importância de alinhar expectativas da automação com as limitações da ferramenta.

---

### Prompt 4 (Contexto aplicado)

Pergunta:
"Quais desafios existem ao testar apps de streaming?"

Resumo da resposta:

* Carregamento de mídia
* Variação de rede
* Comportamento do player

---

### Prompt 5 (Conexão com automação)

Pergunta:
"Como validar reprodução de mídia via automação?"

Resumo da resposta:
A validação deve focar no comportamento do player, não no conteúdo do vídeo.

---

### Prompt 6 (Avançado)

Pergunta:
"Liste cenários de teste para apps de streaming mobile focando em estados do player (play, pause, buffering), incluindo possíveis falhas e estratégias de validação com Appium"

Resumo da resposta:
Cenários estruturados com foco em:

* mudança de estado do player
* falhas de carregamento
* sincronização

---

### 🧠 Principais Aprendizados

* Prompts genéricos geram respostas superficiais
* A inclusão de contexto técnico melhora significativamente os resultados
* Especificar ferramenta e cenário torna as respostas mais aplicáveis
* A qualidade das respostas está diretamente ligada à clareza do prompt

---

### ⚠️ Dificuldades Encontradas

* Necessidade de refinar prompts para obter respostas úteis
* Respostas iniciais pouco aplicáveis
* Falta de exemplos técnicos em algumas interações
* Necessidade de interpretar e adaptar o conteúdo gerado

---

### 💡 Aplicação Prática

Exemplo de cenário adaptado:

Cenário sugerido:

* Validar mudança de estado do player após interação

Adaptação para automação:
A validação pode ser feita verificando a visibilidade do botão de pausa após o clique em "play", utilizando waits explícitos para garantir sincronização.

---

## 📖 Miniguia de Estudo

### 🧩 Resumo

O Appium é uma ferramenta open source para automação de testes mobile que permite validar aplicações nativas, híbridas e web.

Seu funcionamento é baseado em um servidor que recebe comandos e os executa em dispositivos reais ou emuladores por meio de drivers específicos.

Em aplicações de streaming, a automação deve priorizar a validação do comportamento da interface e dos estados do player, pois a validação direta do conteúdo de mídia não é suportada.

---

### 📚 Glossário

* Appium Server: executa comandos de automação
* Desired Capabilities: configurações de sessão
* Driver: interação com o dispositivo
* Locator: identificação de elementos
* Waits: sincronização
* Flakiness: instabilidade dos testes
* Buffering: carregamento de mídia

---

## 🧪 Cenários de Teste Automatizáveis

### Cenário: Reprodução de conteúdo

Dado que o usuário seleciona um conteúdo
Quando clica em "play"
Então o player deve iniciar a reprodução

---

### Cenário: Pausar conteúdo

Dado que o conteúdo está em reprodução
Quando o usuário clica em "pause"
Então a reprodução deve ser interrompida

---

### Cenário: Retomar conteúdo

Dado que o conteúdo está pausado
Quando o usuário clica em "play"
Então o conteúdo deve continuar

---

### Cenário: Navegação até conteúdo

Dado que o usuário está na tela inicial
Quando navega até uma categoria
E seleciona um conteúdo
Então deve visualizar os detalhes

---

### Cenário: Continuação de conteúdo

Dado que o usuário iniciou um conteúdo
E saiu da aplicação
Quando retorna
Então o conteúdo deve aparecer na seção "continuar assistindo"

---

### Cenário: Falha de carregamento

Dado que a conexão está instável
Quando o usuário tenta reproduzir
Então o app deve exibir estado de erro ou carregamento

---

## 💻 Exemplo Técnico

```java
// Localiza botão de play e executa ação
MobileElement playButton = driver.findElementByAccessibilityId("play_button");
playButton.click();

// Aguarda o botão de pause aparecer (indicando início da reprodução)
WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
wait.until(ExpectedConditions.visibilityOfElementLocated(
    MobileBy.AccessibilityId("pause_button")
));
```

---

## ⚠️ Riscos e Limitações

* Não é possível validar o conteúdo do vídeo diretamente
* Dependência de condições de rede
* Instabilidade de elementos do player
* Flakiness nos testes automatizados
* Custo de manutenção dos testes
* Necessidade de ambiente controlado

---

## 🧱 Estrutura de Projeto

src/
├── tests/ → cenários de teste
├── pages/ → representação das telas (Page Object Model)
├── drivers/ → configuração de drivers
└── utils/ → utilitários e helpers

---

## 🚀 Próximos Passos

* Automatizar fluxo completo de reprodução
* Implementar Page Object Model completo
* Melhorar estratégias de sincronização
* Simular condições de rede
* Integrar testes com CI/CD

---

## 🧠 Conclusão

O desenvolvimento deste projeto reforçou a importância de alinhar as expectativas da automação com as limitações da ferramenta, especialmente em cenários com mídia e comportamento assíncrono.

A prática também evidenciou a necessidade de estruturar bem os testes e utilizar estratégias adequadas de sincronização para garantir maior confiabilidade.
