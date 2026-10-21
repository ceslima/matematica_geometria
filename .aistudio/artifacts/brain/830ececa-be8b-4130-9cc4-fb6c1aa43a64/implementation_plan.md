# EuclidesLab — Laboratório Interativo de Geometria Plana

Uma plataforma educacional visual e interativa para o aprendizado de Geometria Plana, combinando um quadro dinâmico de manipulação geométrica em tempo real, exploradores visuais de teoremas clássicos, desafios práticos passo a passo e integração direta com o Google Drive para salvar construções geométricas e exportar cadernos de revisão.

---

## Revisão do Usuário & Decisões Críticas

> [!IMPORTANT]
> Como as perguntas iniciais foram puladas, adotamos as opções recomendadas para entregar a experiência mais completa e versátil possível. Revise as decisões abaixo antes de prosseguirmos com a construção.

- **Público-Alvo e Escopo Pedagógico (Padrão Recomendado)**: Abrangência completa para **Ensino Fundamental II, Ensino Médio e Preparação para Vestibulares/ENEM**, progredindo desde conceitos fundamentais (ângulos, triângulos e polígonos) até relações métricas, circunferências e teoremas clássicos.
- **Ferramentas Interativas Incluídas (Padrão Recomendado)**:
  1. **Quadro Geométrico Interativo (Sandbox)**: Arraste vértices em tempo real com cálculo instantâneo de lados, alturas, ângulos internos, área e perímetro.
  2. **Explorador Visual de Teoremas**: Demonstrações interativas manipuláveis para o Teorema de Pitágoras (áreas dos quadrados nos catetos e hipotenusa), Teorema de Tales (feixe de retas paralelas), Soma dos Ângulos Internos e Círculo/Pi.
  3. **Desafios Práticos e Quizzes**: Problemas visuais contextualizados com validação passo a passo e dicas geométricas.
- **Integração com Google Drive (Padrão Recomendado)**: Uso do escopo de privilégio mínimo `drive.file` para permitir que o estudante **salve e carregue seus projetos/construções geométricas (`.json`)** diretamente no Google Drive, além de **exportar cadernos de estudo e resumos de fórmulas** para sua conta Google, com confirmação explícita antes de qualquer sobrescrita ou exclusão de arquivo.

---

## 1. Visão Geral & Conceito Principal

- **O Que o Aplicativo Faz**: Transforma fórmulas abstratas de geometria plana em objetos visuais táteis. Ao mover um vértice de um triângulo ou ajustar o raio de uma circunferência, o aluno observa instantaneamente como a área, o perímetro, as alturas, as medianas e os ângulos se comportam matematicamente.
- **Público-Alvo / Persona**: Estudantes do ensino básico ao pré-vestibular que precisam visualizar propriedades geométricas para compreender deduções, e professores que desejam demonstrar teoremas em sala de aula e compartilhar atividades via Google Drive.
- **Valor Principal**: Elimina a memorização mecânica de fórmulas ao conectar a manipulação espacial direta no canvas com a expressão algébrica em tempo real e persistência em nuvem no Google Drive.

---

## 2. Experiência do Usuário & Design Visual

### Fluxos Principais do Usuário

1. **Exploração Imediata no Laboratório (Zero-State)**:
   - O usuário abre o aplicativo diretamente na bancada interativa dividida em duas zonas: à esquerda, a **Tela de Construção Cartesiana (65% da largura)** com malha quadriculada de precisão; à direita, o **Deck de Controle e Fórmulas (35% da largura)**.
   - O usuário seleciona uma figura (Triângulo, Quadrilátero/Trapézio, Polígono Regular, Circunferência) ou arrasta diretamente os vértices $A, B, C$ no plano cartesiano e vê os cálculos de área, perímetro, ângulos internos e classificação (ex.: *Triângulo Acutângulo Isósceles*) atualizarem em tempo real.
2. **Laboratório de Teoremas Visuais**:
   - Na aba **Teoremas**, o usuário alterna entre provas visuais interativas:
     - *Teorema de Pitágoras*: Visualização geométrica dos quadrados projetados sobre os lados $a$, $b$ e $c$, permitindo alterar os catetos por controles deslizantes rotulados e comprovar visualmente que $a^2 + b^2 = c^2$.
     - *Teorema de Tales*: Manipulação da posição de retas paralelas cortadas por transversais, exibindo a proporcionalidade constante entre os segmentos.
     - *Polígonos e Soma Angular*: Decomposição visual de um polígono de $n$ lados em $(n - 2)$ triângulos a partir de um vértice.
3. **Prática Guiada & Desafios**:
   - Na aba **Desafios**, o aluno resolve problemas interativos (tanto de cálculo quanto de construção, como *"Ajuste o vértice C no plano para formar um triângulo retângulo de área igual a 24 u²"*), recebendo feedback visual imediato no próprio diagrama e explicação detalhada passo a passo.
4. **Sincronização e Exportação com Google Drive**:
   - Na aba ou gaveta **Meus Arquivos (Google Drive)**, o usuário autentica com sua conta Google ("Sign in with Google") para salvar suas construções geométricas personalizadas, recarregar cenas salvas anteriormente, exportar um **Caderno de Fórmulas e Resolução** para o seu Drive, ou gerenciar seus arquivos salvos (com modal de confirmação obrigatório antes de atualizar ou excluir qualquer arquivo existente).

### Identidade Visual & Tema

- **Direção Estética**: *Editorial Arquitetônico & Caderno de Precisão Matemática* — inspirado em pranchetas técnicas modernas, diagramas clássicos de Euclides renovados com design digital limpo e alto contraste pedagógico.
- **Regra da Barra Superior (Top Bar Contract)**:
  - Segue estritamente o contrato de linha única e 3 zonas separadas por espaçamento amplo (`gap-8`):
    1. **Marca**: `EuclidesLab` em tipografia display limpa e sem subtítulos acoplados.
    2. **Navegação (4 links concisos em linha única)**: `Laboratório`, `Teoremas`, `Desafios`, `Biblioteca de Fórmulas`.
    3. **Ação Primária**: Botão único de sincronização/conexão com o **Google Drive** (ou acesso aos projetos salvos quando autenticado).
- **Paleta de Cores (Orçamento 60-30-10)**:
  - **60% Canvas Dominante (`--background`)**: Papel técnico claro e suave (`#F8FAFC`) com grade cartesiana sutil (`#E2E8F0`) para leitura confortável e sem fadiga visual.
  - **30% Superfícies Estruturais e Painéis**: Painéis brancos puros (`#FFFFFF`) delimitados por bordas de espessura fina (`1px solid #E2E8F0`), tipografia principal em ardósia profundo (`#0F172A`) e metadados não encapsulados em cinza técnico (`#475569`).
  - **10% Acentos Semânticos Focais**:
    - *Azul Cobalto Geométrico (`#0284C7`)*: Vértices ativos, segmentos principais e controles primários (`● ATIVO`).
    - *Esmeralda de Validação (`#059669`)*: Propriedades verificadas, ângulos retos ($90^\circ$) e respostas corretas (`✓ VERIFICADO`).
    - *Âmbar Solar (`#D97706`)*: Projeções auxiliares, alturas, bissetrizes e dicas visuais (`▲ AUXILIAR`).
- **Tipografia & Hierarquia (Regra 2+1 Fontes)**:
  - *Display / Títulos*: **Bricolage Grotesque** (SemiBold/Bold) para cabeçalhos de módulos e nomes de teoremas com personalidade geométrica.
  - *Corpo / Explicações*: **Plus Jakarta Sans** (Regular/Medium) para enunciados claros e anotações conceituais.
  - *Matemática, Coordenadas e Métricas*: **IBM Plex Mono** com numerais tabulares (`tabular-nums`) para coordenadas $(x, y)$, medidas de ângulos, áreas e equações algébricas, garantindo alinhamento vertical perfeito enquanto os números mudam ao arrastar vértices.
- **Feedback Interativo & Movimento**:
  - Resposta instantânea ($<16\text{ms}$) durante o arraste de vértices em SVG/Canvas com *snap-to-grid* (imã de grade opcional) para facilitar a criação de medidas inteiras e triângulos pitagóricos.
  - Nenhum metadado estático usará "pílulas" (badges arredondadas); classificações geométricas e unidades serão exibidas em linha com separadores tipográficos limpos (`Triângulo Retângulo · Área: 24.0 u² · Perímetro: 24.0 u`).

---

## 3. Decisões de Produto & Trade-Offs

- **Decisão 1: Motor Gráfico Vetorial Interativo (SVG de Alta Precisão com Coordenadas Cartesianas)**
  - *Abordagem Escolhida*: Renderização baseada em SVG interativo acoplado ao estado reativo com suporte a eventos de ponteiro (`pointerdown`, `pointermove`, `pointerup`), *snap-to-grid* configurável e camadas dedicadas para malha, arcos de ângulos, cotas de dimensão e pontos de controle.
  - *Por Quê*: Diferente de um `<canvas>` bitmap opaco, o SVG garante nitidez vetorial infinita para textos matemáticos, arcos de ângulos, símbolos de ângulo reto ($\perp$) e acessibilidade direta via DOM em qualquer resolução de tela (1440px desktop ou tablet).
  - *Alternativas Consideradas*: Bibliotecas 3D pesadas (Three.js) ou Canvas 2D puro foram descartados para o quadro principal por dificultarem a estilização tipográfica nítida de cotas, rótulos de vértices e interação acessível por elemento.
- **Decisão 2: Integração com Google Drive via Escopo `drive.file` e Cache de Token em Memória**
  - *Abordagem Escolhida*: Autenticação client-side via Firebase Auth (`GoogleAuthProvider`) solicitando exclusivamente o escopo `https://www.googleapis.com/auth/drive.file`, mantendo o token de acesso estritamente em memória e exigindo confirmação explícita em modal antes de qualquer atualização ou exclusão de arquivos no Drive.
  - *Por Quê*: Segue o princípio de menor privilégio (acessa apenas os arquivos criados pelo próprio aplicativo de geometria), protege a privacidade do estudante e evita erros de redirecionamento OAuth em ambientes dinâmicos.

---

## 4. Arquitetura Técnica & Estratégia de Dados

### Diagrama de Arquitetura e Hierarquia de Componentes

```
┌────────────────────────────────────────────────────────────────────────────┐
│                        Barra Superior (3 Zonas)                            │
│  [EuclidesLab]     [Laboratório | Teoremas | Desafios | Fórmulas]   [Drive]│
└───────────────────────────────────────┬────────────────────────────────────┘
                                        │
        ┌───────────────────────────────┼───────────────────────────────┐
        ▼                               ▼                               ▼
┌───────────────────────┐   ┌───────────────────────┐   ┌───────────────────────┐
│  Bancada Geométrica   │   │ Explorador de Teoremas│   │  Desafios & Fórmulas  │
│  (Layout 2 Zonas)     │   │ (Provas Manipuláveis) │   │ (Prática Interativa)  │
├───────────────────────┤   ├───────────────────────┤   ├───────────────────────┤
│ • Palco Cartesiano    │   │ • Pitágoras Visual    │   │ • Desafios de Ajuste  │
│   SVG (65% Largura)   │   │   (Quadrados nos Lados│   │   no Canvas + Quizzes │
│ • Vértices Arrastáveis│   │ • Teorema de Tales    │   │ • Validador Passo a   │
│   com Snap-to-Grid    │   │   (Feixe de Paralelas)│   │   Passo com Dicas     │
│ • Deck de Controle e  │   │ • Polígonos Regulares │   │ • Catálogo Interativo │
│   Fórmulas Ao Vivo    │   │   & Circunferência/Pi │   │   de Geometria Plana  │
└───────────┬───────────┘   └───────────┬───────────┘   └───────────┬───────────┘
            │                           │                           │
            └───────────────────────────┼───────────────────────────┘
                                        ▼
┌────────────────────────────────────────────────────────────────────────────┐
│              Motor Matemático & Gerenciador de Estado Geométrico           │
│ • Cálculo vetorial em tempo real (distâncias, ângulos, baricentro, alturas)│
│ • Serialização de construções geométricas e progresso de desafios          │
└───────────────────────────────────────┬────────────────────────────────────┘
                                        ▼
┌────────────────────────────────────────────────────────────────────────────┐
│           Camada de Integração Google Workspace (Google Drive API)         │
│ • Autenticação Firebase + GoogleAuthProvider (Token em memória)            │
│ • Salvar/Carregar projetos geométricos (.json) e Cadernos de Estudo (.md)  │
│ • Modal de Confirmação Obrigatório para sobrescrita ou exclusão no Drive   │
└────────────────────────────────────────────────────────────────────────────┘
```

### Modelo de Dados e Estado

- **Cena Geométrica (`GeometryScene`)**:
  - `id`, `title`, `shapeType` (`triangle` | `quadrilateral` | `regularPolygon` | `circle` | `transversal`), `vertices` (lista de coordenadas `{ id, label, x, y }`), `parameters` (raio, número de lados, escala da malha, visibilidade de alturas/bissetrizes/mediatrizes), e `notes` (anotações do estudante).
- **Métricas Derivadas em Tempo Real (`ComputedGeometryMetrics`)**:
  - Comprimentos dos lados, ângulos internos em graus, área (via fórmula de Shoelace / determinantes ou $\pi r^2$), perímetro, coordenadas do baricentro/circuncentro, classificação automática da figura e passo a passo da fórmula aplicada com os valores atuais substituídos.
- **Progresso e Desafios (`ChallengeItem`)**:
  - Enunciado contextualizado, meta geométrica verificável (ex.: construir figura com área ou ângulo específico, ou resolver questão calculada), dicas progressivas, explicação completa e status de conclusão.
- **Arquivo Sincronizado (`DriveProjectFile`)**:
  - Metadados do arquivo no Google Drive (`id`, `name`, `modifiedTime`, `mimeType`) vinculados às construções salvas pelo usuário ou aos resumos exportados.

### Mapeamento de Componentes Interativos e Mutação de Estado

- **Interação de Arraste no Palco (`InteractiveCanvas`)**:
  - Ao arrastar qualquer vértice ($A, B, C, D$) ou controle deslizante, o estado das coordenadas atualiza instantaneamente (com opção de *Snap to Grid* de $0.5$ ou $1.0$ unidade), recalculando todas as cotas visuais, arcos de ângulo e equações exibidas no painel lateral.
- **Controles de Camadas Didáticas (`ConceptDeck`)**:
  - Botões de alternância ativam/desativam elementos auxiliares sobre a figura (mostrar alturas, mostrar ângulos internos, mostrar circunferência circunscrita, mostrar decomposição em triângulos) e permitem carregar predefinições clássicas (ex.: *Triângulo Pitagórico 3-4-5*, *Triângulo Equilátero*, *Trapézio Isósceles*, *Hexágono Regular*).
- **Fluxo de Persistência e Confirmação no Google Drive (`DriveSyncModal`)**:
  - Permite criar um novo arquivo no Google Drive (`POST https://www.googleapis.com/upload/drive/v3/files?uploadType=multipart`), listar e abrir construções salvas pelo app (`GET https://www.googleapis.com/drive/v3/files`), ou atualizar/excluir um arquivo existente mediante confirmação explícita em um diálogo dedicado detalhando o nome do arquivo afetado.
