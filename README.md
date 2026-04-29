# Pesquisa de acessibilidade
  

## Sobre esta pesquisa 
   Uma análise prática sobre acessibilidade web — investigando quais ferramentas de auditoria existem, 
   como cada uma funciona e o que elas revelam sobre os sites que usamos no dia a dia. 
 
## O que descobrimos (Principais Achados)
> Fonte: https://webaim.org/projects/million/

   Os tipos de erro mais comuns foram:
   - Baixo contraste de texto (81% das páginas)
   - Atributos alt ausentes em imagens (54% das páginas)
   - Labels ausentes em campos de formulário (48% das páginas)
   - Links vazios ou sem descrição (44% das páginas)
   - Botões sem nome acessível (28% das páginas)
  
 
## Ferramentas
   ### 1. NVDA (NonVisual Desktop Access)
Diferente das outras, esta não é uma ferramenta de auditoria, mas um **leitor de tela gratuito e de código aberto** para Windows.

- **Como funciona:** Ele traduz a interface visual em som. O NVDA lê o "HTML semântico" e as propriedades de acessibilidade (como ARIA) para transmitir ao usuário o que está na tela via síntese de voz ou braille.
- **O que detecta:** Falhas de navegação por teclado, ordem lógica de leitura, se os elementos interativos (botões, links) estão bem descritos e se o conteúdo dinâmico (pop-ups, alertas) é anunciado.
- **O que descobrimos:** A experiência real. Descobrimos se o site é funcional ou se é uma "armadilha de teclado" onde o usuário fica preso em um menu, por exemplo.

---

### 2. Lighthouse
Uma ferramenta automatizada e integrada diretamente ao Google Chrome (`Inspect > Lighthouse`).

- **Como funciona:** Ele executa uma série de testes programáticos baseados nas diretrizes do WCAG (Web Content Accessibility Guidelines) e gera uma nota de 0 a 100.
- **O que detecta:** Problemas técnicos "óbvios", como falta de atributo `alt` em imagens, baixo contraste de cores, ausência de idioma no documento (`lang="pt"`) e hierarquia de títulos (H1, H2...) quebrada.
- **O que descobrimos:** Uma linha de base rápida. Ele é ótimo para pegar erros básicos de desenvolvimento antes mesmo de o site ir ao ar.

---

### 3. Axe DevTools
Considerada por muitos especialistas como a ferramenta automatizada mais precisa do mercado.

- **Como funciona:** É uma extensão de navegador que analisa o DOM (o código da página) em busca de violações. Ela é famosa por ter "zero falso-positivos", ou seja, se ela aponta um erro, ele realmente existe.
- **O que detecta:** Tudo o que o Lighthouse detecta, mas com uma análise mais profunda de componentes complexos (como menus e modais). A versão paga oferece testes guiados que ajudam a analisar o que o robô não consegue sozinho.
- **O que descobrimos:** Erros críticos de código. Ele fornece links diretos para a documentação técnica, explicando *por que* o erro é um problema e *como* corrigi-lo.

---

### 4. WAVE (Web Accessibility Evaluation Tool)
Uma ferramenta visual poderosa, muito usada para auditorias rápidas e por designers.

- **Como funciona:** Ao ativar a extensão, o WAVE injeta ícones diretamente sobre a sua página. Se um botão não tem nome, um ícone de erro aparece em cima dele.
- **O que detecta:** Estrutura de cabeçalhos, contraste visual, erros de formulário (labels faltando) e redundâncias. Ele permite desativar o CSS da página para ver se a ordem de leitura faz sentido sem o design.
 
## Como isso afeta o nosso trabalho como desenvolvedores 
   O erro mais comum é tratar acessibilidade como uma fase de homologação (QA), algo que você verifica no final. Isso gera retrabalho. A abordagem correta é tratar cada critério de acessibilidade como essencial já no começo.

**Exemplo de critério de aceite:**
> "Quando o formulário de cadastro é renderizado, e submeto com campos vazios, cada mensagem de erro deve ser associada ao campo correspondente e anunciada pelo leitor de tela."

> O atributo `aria-describedby` pode ser usado para garantir a leitura correta pelo leitor de tela.

Baseado no que as ferramentas revelam com mais frequência, estas são as três ações de maior impacto:

---

**Prática 1: a mais simples — Instale a extensão Axe DevTools agora.**

Está disponível gratuitamente para Chrome. Rode em qualquer projeto em que você está trabalhando hoje e observe quantos erros aparecem.

**Prática 2: teste de teclado — Navegue pelo seu projeto usando apenas o teclado.**

Use `Tab` para avançar entre elementos, `Shift+Tab` para voltar e `Enter`/`Espaço` para ativar. Perguntas-guia: consigo completar o fluxo principal sem usar o mouse? O outline (focus) está sempre visível?

**Prática 3: imagens importantes precisam ser explicadas — Adicione texto alternativo real às imagens.**

`alt=""` é correto para imagens decorativas. `alt` descritivo é obrigatório para imagens que comunicam informação. Um leitor de tela que encontra `alt="lucasfabiano.jpg"` ou `alt="foto ae"` não entrega nenhuma informação útil ao usuário.
 
## Referências

### WCAG

- W3C. *WCAG 2.1 – Web Content Accessibility Guidelines*. 2018. https://www.w3.org/TR/WCAG21/

- W3C. *WCAG 2.2 – Web Content Accessibility Guidelines*. 2023. https://www.w3.org/TR/WCAG22/

- WebAIM. *WCAG 2 Checklist*. s.d. https://webaim.org/standards/wcag/checklist

- W3C. *Understanding WCAG 2.1*. 2018. https://www.w3.org/WAI/WCAG21/Understanding/

- W3C. *WCAG Quick Reference*. s.d. https://www.w3.org/WAI/WCAG21/quickref/

### Pesquisas e Relatórios

- WebAIM. *The WebAIM Million – The 2026 report on the accessibility of the top 1,000,000 home pages*. 2026. https://webaim.org/projects/million/

- WebAIM. *Screen Reader User Survey #10*. 2024. https://webaim.org/projects/screenreadersurvey10/

### Ferramentas de Teste

- Google. *Lighthouse*. s.d. https://developer.chrome.com/docs/lighthouse/

- WebAIM. *WAVE – Web Accessibility Evaluation Tool*. s.d. https://wave.webaim.org/

- Deque Systems. *Axe DevTools*. s.d. https://www.deque.com/axe/devtools/

- Deque Systems. *axe-core*. s.d. https://github.com/dequelabs/axe-core

### Leitores de Tela

- NV Access. *NVDA – NonVisual Desktop Access*. s.d. https://www.nvaccess.org/

- Apple. *VoiceOver*. s.d. https://www.apple.com/accessibility/vision/

- Freedom Scientific. *JAWS*. s.d. https://www.freedomscientific.com/products/software/jaws/

### Referências Gerais

- W3C. *WAI – Web Accessibility Initiative*. s.d. https://www.w3.org/WAI/

- WebAIM. *Web Accessibility In Mind*. s.d. https://webaim.org/

- Mozilla. *MDN Web Docs – Accessibility*. s.d. https://developer.mozilla.org/en-US/docs/Web/Accessibility

- Deque Systems. *Deque University*. s.d. https://dequeuniversity.com/

- A11Y Project. *The A11Y Project*. s.d. https://www.a11yproject.com/
