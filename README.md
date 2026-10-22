# Currículo Pro para Codex

**Uma Skill para organizar seu perfil profissional, analisar vagas, adaptar currículos com evidências e revisar arquivos DOCX e PDF.** Funciona em português e pode preparar currículos em outros idiomas conforme a vaga.

> A Skill não promete aprovação em sistemas ATS nem inventa experiências, competências ou resultados. O perfil profissional mestre conserva os fatos; cada currículo adaptado é uma versão separada para uma oportunidade.

## O que ela faz

A Skill curriculo conduz o processo completo:

1. Organiza seu currículo original em um perfil profissional mestre e registra a origem de cada informação.
2. Analisa a descrição da vaga e separa exigências obrigatórias, desejáveis, responsabilidades e palavras-chave.
3. Apresenta diagnóstico, matriz de aderência, lacunas e alterações propostas antes da adaptação.
4. Adapta o currículo com base em evidências e no idioma e país da vaga.
5. Revisa realizações, estrutura ATS, consistência, gramática e afirmações sem comprovação.
6. Gera DOCX e PDF e orienta a conferência da ordem de leitura, conteúdo e paginação.

## Instalação

### Opção A: baixar o ZIP

1. Nesta página do GitHub, clique em **Code → Download ZIP** e extraia o arquivo.
2. Abra o PowerShell na pasta extraída.
3. Revise o instalador (instalar.ps1) e execute:


    powershell -NoProfile -ExecutionPolicy Bypass -File .\instalar.ps1

O instalador copia somente a pasta da Skill para ~/.codex/skills/curriculo (ou $env:CODEX_HOME\skills\curriculo, se CODEX_HOME estiver definido). Se já houver uma versão instalada, ela é guardada em uma pasta de backup com data e hora. O script não baixa nem instala dependências.

### Opção B: instalar manualmente

Copie skills/curriculo para a pasta de Skills do Codex:

- Windows: %USERPROFILE%\.codex\skills\curriculo
- macOS/Linux: ~/.codex/skills/curriculo
- Se você definiu CODEX_HOME, use $CODEX_HOME/skills/curriculo.

A pasta final deve conter SKILL.md diretamente dentro dela. Abra uma nova conversa no Codex para a Skill ser reconhecida. Se ela não aparecer, reinicie o Codex e tente novamente.

## Como chamar a Skill

Você pode chamá-la pelo nome, com $curriculo quando o seletor de Skills do Codex estiver disponível, ou simplesmente pedir uma tarefa de currículo em linguagem natural. Se a Skill estiver instalada e o Codex não a selecionar automaticamente, escreva: Use a Skill curriculo.

## Passo a passo recomendado

### 1. Criar o perfil profissional mestre

Anexe seu currículo original e use:

    $curriculo
    Leia meu currículo e organize um perfil profissional mestre reutilizável.
    Mantenha cada afirmação ligada ao trecho ou arquivo de origem e classifique-a
    como comprovada, declarada sem documento, ambígua ou ausente. Preserve cargos,
    datas e escopo. Liste contradições e perguntas relevantes. Não adapte para uma
    vaga e não gere DOCX/PDF ainda.

Revise os dados e responda às perguntas antes de reutilizar esse perfil. O perfil pode ser mantido como um arquivo local Markdown ou JSON; peça ao Codex para salvá-lo numa pasta privada de trabalho, fora do repositório público.

### 2. Analisar a vaga e medir a aderência

Cole a descrição da vaga ou anexe o arquivo e peça:

    $curriculo
    Analise esta vaga. Separe requisitos obrigatórios, desejáveis,
    responsabilidades e palavras-chave. Para cada requisito, cite a evidência
    correspondente no meu perfil mestre ou marque como lacuna/pendência. Apresente
    um diagnóstico, uma matriz de aderência, as perguntas que preciso responder e
    uma proposta de adaptação. Ainda não gere os documentos finais.

### 3. Revisar a proposta

Confira datas, títulos, responsabilidades, tecnologias, níveis e resultados. Corrija qualquer interpretação imprecisa e responda apenas às perguntas para as quais tiver informação. Peça que a Skill atualize a matriz e a proposta.

### 4. Gerar o currículo da vaga

Depois de aprovar o conteúdo, peça:

    $curriculo
    Com base no perfil mestre e na proposta que revisei, prepare meu currículo
    para esta vaga em [português do Brasil/inglês dos Estados Unidos/etc.]. Preserve
    os fatos e a cronologia, use uma coluna e títulos convencionais para ATS, e
    mantenha o perfil mestre intacto. Gere DOCX e PDF, relatório de auditoria ATS,
    matriz requisito versus evidência, registro das principais alterações e
    sugestões futuras. Antes de entregar, confira texto extraído, ordem de leitura,
    paginação e renderização de todas as páginas. Informe qualquer verificação que
    não puder realizar.

Substitua o idioma e país entre colchetes. Para adaptar a outra vaga depois, reutilize o mesmo perfil mestre e inicie uma nova matriz. Não use um currículo adaptado anterior como fonte principal de fatos.

## Privacidade e integridade

- Trabalhe com cópias locais dos currículos. Não coloque seu perfil mestre ou currículo pessoal neste repositório público.
- A Skill não envia arquivos a serviços externos por conta própria. Confirme antes de usar integrações externas que processem seus dados.
- Valores, métricas e resultados só entram quando você os forneceu e pode atribuí-los à sua atuação.
- Conhecimento básico, curso ou menção a uma ferramenta não viram experiência avançada.
- Para a versão ATS, prefira coluna única, texto selecionável e títulos simples. Não inclua foto nem dados pessoais sem necessidade específica.
- O resultado é uma revisão heurística de legibilidade e aderência. Cada empresa configura seus sistemas de seleção de forma diferente.

## Estrutura do repositório

- skills/curriculo/SKILL.md: instruções completas da Skill única.
- instalar.ps1: instalador local para Windows.
- resume-toolkit/: auditor determinístico, testes e exemplos de avaliação semântica.

Os scripts auxiliares podem ser executados com Python 3 padrão, sem instalar pacotes:

    python -m unittest discover -s resume-toolkit/tests -v
    python resume-toolkit/scripts/audit_resume.py caminho\curriculo.docx --terms Python SQL

O auditor sinaliza texto vazio, termos ausentes, possíveis placeholders e métricas para conferência humana. Ele não mede aderência semântica nem prevê aprovação em ATS. A extração de texto de PDF pode exigir PyMuPDF ou pdftotext; a revisão visual das páginas continua necessária.

## Licença

Nenhuma licença de reutilização foi especificada. A visibilidade pública permite ler o repositório, mas não concede automaticamente permissão para copiar, modificar ou redistribuir o conteúdo. Uma licença poderá ser adicionada quando o titular escolher os termos.
