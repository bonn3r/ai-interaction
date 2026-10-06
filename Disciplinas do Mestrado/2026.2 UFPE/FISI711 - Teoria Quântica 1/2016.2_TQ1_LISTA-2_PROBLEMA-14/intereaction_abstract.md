# Interações com IA para construir o código solicitado pelo professor Renê

### Introdução

Utilizando as IA... bla bla bla


## **1.** Resumo da interação com o Claude Code (Gerado pelo Assistente IA)

### **1.1** Contexto

Atividade avaliativa de FISI 711 (Teoria Quântica I, UFPE): construir uma página HTML que anima a evolução temporal de combinações lineares de autoestados do oscilador harmônico unidimensional, com três modos de operação e opções configuráveis pelo usuário.

### **1.2** O que foi desenvolvido
- Uma página HTML/CSS/JS autocontida que calcula os autoestados do oscilador harmônico via recursão numérica estável e evolui os coeficientes no tempo, exibindo partes real/imaginária da função de onda e a densidade de probabilidade em dois gráficos animados.
- Suporte aos três modos pedidos: autoestado puro, combinação de dois autoestados com amplitudes iguais, e estado coerente com número médio de quanta escolhido pelo usuário.
- Interface com controles de seleção de modo, parâmetros de cada caso, velocidade de animação, play/pause e reset.
- A pedido, o código foi reorganizado em três blocos separados (HTML, CSS e JavaScript), com a ressalva de que a entrega final da disciplina deve ser o arquivo `.html` único.

### **1.3** Tentativa não concluída
Houve um pedido para adaptar o layout ao site pessoal do usuário (Q-Science, hospedado no GitHub Pages/GitHub). Não foi possível obter o HTML/CSS reais do site devido a restrições de acesso automatizado ao repositório; ficou pendente o usuário fornecer os arquivos-fonte (colados, via link raw do GitHub, ou por upload) para que a adaptação visual seja feita com fidelidade ao design original.

### **1.4** Link para interação

A interação está disponível [aqui](https://claude.ai/share/4ed9232a-d6f3-4d34-89ad-12cd30e0e1ef).

## **2** Resumo da interação com o Deepseek (Gerado pelo Assistente IA)

### **2.1** Verificação dos requisitos do problema
Foram identificados os pontos obrigatórios: animação da evolução temporal de estados do oscilador harmônico unidimensional, exibição da função de onda (partes real e imaginária) e da densidade de probabilidade, escolha entre autoestado puro, combinação de dois autoestados com amplitudes iguais e estado coerente com \(\langle n\rangle\) ajustável, além do nome no título da página.

### **2.2** Análise do código original
O HTML inicial cumpria os requisitos essenciais, mas apresentava falhas: bug no redimensionamento dos canvases (altura dobrava a cada resize), falta de normalização no modo (b) quando \(n_1 = n_2\), ausência de controle de fase relativa em (b) e de fase para \(\lambda\) em (c). Foram sugeridas correções pontuais.

### **2.3** Separação em HTML, CSS e JavaScript
O código foi dividido em três partes distintas — estrutura, estilo e lógica — mantendo a mesma funcionalidade e facilitando a manutenção.

### **2.4** Adaptação visual ao site Q-Science
A aparência foi alinhada ao site do usuário: uso das variáveis CSS do tema (modo claro e escuro), fontes Open Sans e Roboto Slab, botão de alternância de tema com persistência em `localStorage`, layout responsivo e componentes visuais coerentes com o template Editorial.

### **2.5** Integração do MathJax v3
Foi adicionado suporte a LaTeX via MathJax v3, com conversão de rótulos estáticos e atualização dinâmica de valores numéricos. Incluiu-se tratamento para o modo escuro e inicialização sincronizada com o loop de animação.

### **2.6** Revisão do arquivo modificado manualmente
O usuário enviou uma versão alterada do HTML. Foram apontadas inconsistências: rótulo duplicado antes do fieldset de animação, uso de `</br>` em vez de `<br>`, `<strong>` dentro de spans que são sobrescritos pelo JavaScript, falta de padronização em `phival`, divergência entre “Wilian” e “Willian”, fonte Inconsolata não carregada e possível erro no nome do docente.

### **2.7** Correções no script Python (comparacao.html)
O script gerava um HTML com gráficos em escala fixa e problemas de visualização. As correções restringiram-se à parte gráfica: escala vertical de \(\psi\) calculada a partir do máximo real de Re e Im, escala própria para \(|\psi|^2\), preenchimento a partir da base do canvas, suporte a HiDPI e rótulos de escala.

### **2.8** Esclarecimento físico sobre Re, Im e normalização
Discutiu-se que \([\operatorname{Re}\Psi]^2 + [\operatorname{Im}\Psi]^2 = |\Psi(x,t)|^2\), que não é igual a 1 em cada ponto; a normalização \(\int |\Psi|^2 dx = 1\) vale após integração espacial. No autoestado puro, Re e Im oscilam em quadratura com a mesma envoltória; na superposição, há termos de interferência e \(|\Psi|^2\) varia no tempo; no estado coerente, o pacote oscila sem se espalhar.

### **2.9** Verificação da suspeita sobre o problema14_bonner.html
Confirmou-se que a aparente “não variação” da parte real no modo (a) é um artefato da auto-escala dinâmica do eixo vertical: o código recalcula o limite a cada quadro com base no máximo entre Re e Im, mantendo a maior curva sempre com cerca de 87% da meia-altura. A resposta de outra IA foi considerada correta no diagnóstico, mas imprecisa ao afirmar que o eixo acompanha proporcionalmente apenas Re; na verdade, ele segue o máximo entre as duas componentes, e o travamento visual é parcial.

### **2.10** Conclusão
O código calcula corretamente a física; a diferença visual entre os dois HTMLs decorre exclusivamente da estratégia de escala dos gráficos — dinâmica em um caso, fixa no outro.

### **2.11** Link para interação

A interação está disponível [aqui](https://chat.deepseek.com/share/36ij4o6sazlznu6lh6).


## **3** Resumo de outra interação com o Deepseek (Gerado pelo Assistente IA)

### **3.1** Pontos abordados
- O usuário enviou a lista de exercícios `lista2.pdf` e solicitou um código em Python para Jupyter Notebook que resolvesse o **Problema 14**.
- O Problema 14 pede uma animação da evolução temporal de combinações lineares de estados estacionários do oscilador harmônico unidimensional, incluindo autoestado puro, superposição de dois autoestados com amplitudes iguais e estado coerente.
- Inicialmente foi proposta uma solução em HTML/JavaScript para gerar uma página interativa.
- Em seguida, o usuário esclareceu que desejava um código Python para Jupyter Notebook.
- Foi então apresentada uma solução interativa em Python utilizando `numpy`, `scipy`, `matplotlib` e `ipywidgets`, com controles para selecionar o modo, ajustar parâmetros e animar a função de onda (partes real e imaginária) e a densidade de probabilidade.
- Por fim, o usuário solicitou este resumo sintético da interação em formato Markdown.

### **3.2** Link para interação

A interação está disponível [aqui](https://chat.deepseek.com/share/9qf1a4pbpj4l8x52u9).

## **4** Resumo da Interação: Análise e Correção da Simulação do Oscilador Harmônico Quântico (Gerado pelo Gemini)

### **4.1** Validação dos Requisitos
* Verificação do **Problema 14** da disciplina de Teoria Quântica 1, confirmando as exigências do programa em HTML: animação da evolução temporal da função de onda (partes real e imaginária) e da densidade de probabilidade para autoestados puros, superposições e estados coerentes.

### **4.2** Comparação e Diagnóstico dos Códigos
* **Verificação de Validade:** Avaliação de duas versões de código fornecidas, confirmando a validade funcional e conceitual da versão `problema14_bonner.html`.
* **Análise de Falhas do Código Secundário (`comparacao.html`):**
  * Estruturação como script Python em vez de arquivo HTML nativo.
  * Instabilidade numérica na geração dos polinômios de Hermite para valores elevados de $n$.
  * Limite rígido nos eixos espaciais que cortavam a função de onda.

### **4.3** Identificação do Erro Visual de Escala
* **Confirmação da Suspeita do Usuário:** Análise do comportamento visual no modo de autoestado puro.
* **Causa Física/Computacional:** O código `problema14_bonner.html` recalculava a amplitude máxima do eixo vertical a cada quadro (*auto-escala dinâmica*). Esse ajuste contínuo gerava uma compensação automática na escala, impedindo a visualização do crescimento e decrescimento real das partes real e imaginária durante a evolução temporal.

### **4.4** Correção e Solução
* Reformulação da lógica de renderização para calcular e fixar os limites dos eixos no momento da construção do estado (*escala estática por estado*).
* Fornecimento do código HTML/JavaScript corrigido, garantindo a fidelidade física na alternância temporal entre $\operatorname{Re}(\Psi)$ e $\operatorname{Im}(\Psi)$.

### **4.5** Link para interação

A interação está disponível [aqui](https://share.gemini.google/bS6l2dI6oPIC).