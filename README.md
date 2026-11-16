# Modelo Acadêmico Modular em LaTeX (`modelo-academico`)

Este diretório contém uma versão aprimorada, modular e de fácil edição do modelo acadêmico em LaTeX, projetada tanto para **pré-projetos e projetos de pesquisa** quanto para **TCCs, monografias e relatórios científicos**.

Arquivos desta pasta:
- **`modelo.tex`**: Arquivo único autocontido, com painel de controle simplificado (`{sim}` / `{nao}`), motor de formatação isolado e caixa de ferramentas com receitas prontas.
- **`modelo.pdf`**: PDF gerado a partir do `modelo.tex` padrão.

---

## Como começar em 4 passos

1. **Preencha os dados do trabalho (PARTE 1 do `modelo.tex`):**
   Edite apenas o que está entre chaves `{ }` nos comandos `\Instituicao{...}`, `\Autor{...}`, `\Titulo{...}`, `\Natureza{...}`, `\Orientacao{...}`, etc. Campos opcionais deixados vazios (`{}`) ocultam-se sozinhos sem deixar espaços em branco.
2. **Ligue ou desligue páginas e seções (PARTE 2 do `modelo.tex`):**
   Troque `{sim}` por `{nao}` (ou vice-versa) em qualquer opção:
   ```tex
   \MostrarCapa{sim}
   \MostrarFolhaRosto{sim}
   \MostrarDedicatoria{nao}
   \MostrarAgradecimentos{nao}
   \MostrarEpigrafe{nao}
   \MostrarResumo{sim}
   \MostrarAbstract{nao}
   \MostrarListaFiguras{nao}
   \MostrarListaQuadros{nao}
   \MostrarListaTabelas{nao}
   \MostrarListaSiglas{nao}
   \MostrarSumario{sim}
   \MostrarCronograma{sim}
   \MostrarReferencias{sim}
   \MostrarApendices{nao}
   \MostrarAnexos{nao}
   ```
3. **Escreva seus textos (PARTES 3, 4 e 5 do `modelo.tex`):**
   Pule o bloco técnico ("Motor de Formatação") e substitua os campos entre `[COLCHETES]` pelo seu conteúdo.
4. **Gere o PDF:**
   - **Localmente com Tectonic (recomendado):**
     ```bash
     tectonic modelo.tex
     ```
   - **No Overleaf:** vá em *Menu > Compilador* e selecione **XeLaTeX** ou **LuaLaTeX**.

---

## Principais melhorias e atalhos disponíveis

### 1. Estrutura de Seções e Listas Simplificadas
- **Seções numeradas automaticamente:** `\Secao{TÍTULO}`, `\Subsecao{Título}` e `\Subsubsecao{Título}`.
- **Listas prontas com recuo de 1,25 cm:**
  - `\begin{ListaAlfab} ... \end{ListaAlfab}` (alíneas `a)`, `b)`, `c)`)
  - `\begin{ListaNumerada} ... \end{ListaNumerada}` (`1.`, `2.`, `3.`)
  - `\begin{ListaMarcadores} ... \end{ListaMarcadores}` (marcadores)

### 2. Quadros vs. Tabelas (Padrão ABNT / IBGE)
- **Quadro** (fechado com grades laterais — ideal para cronogramas e dados qualitativos/textuais):
  ```tex
  \begin{Quadro}{Título do quadro}{elaboração própria (2026)}{qua:meu-quadro}
    \begin{tabularx}{\linewidth}{|P{4cm}|L|}
      \hline
      \textbf{Coluna 1} & \textbf{Coluna 2} \\ \hline
      Item A & Descrição do item A \\ \hline
    \end{tabularx}
  \end{Quadro}
  ```
- **Tabela** (aberta nas laterais, padrão IBGE — ideal para dados numéricos e estatísticos):
  ```tex
  \begin{Tabela}{Título da tabela}{dados da pesquisa (2026)}{tab:minha-tabela}
    \begin{tabularx}{\linewidth}{L c c c}
      \hline
      \textbf{Amostra} & \textbf{Parâmetro 1} & \textbf{Parâmetro 2} & \textbf{Média} \\ \hline
      Amostra A & 10,5 & 2,3 & 10,5 \\ \hline
    \end{tabularx}
  \end{Tabela}
  ```
- **Tipos de colunas simplificados:**
  - `L`, `C`, `R`: colunas elásticas que quebram linha automaticamente (alinhadas à esquerda, centro ou direita).
  - `P{4cm}`: coluna de largura fixa alinhada à esquerda.
  - `M{1.4cm}`: coluna de largura fixa centralizada horizontal e verticalmente.

### 3. Figuras com Proteção contra Arquivos Ausentes
```tex
\InserirFigura
  {Título da figura}
  {imagens/exemplo.png}
  {0.7\linewidth}
  {elaboração própria (2026)}
  {fig:exemplo}
```
Se a imagem ainda não existir na pasta, o documento **não falha na compilação**: ele desenha um aviso visual no PDF indicando onde colocar o arquivo.

### 4. Citação Direta Longa (> 3 linhas)
```tex
\begin{CitacaoLonga}
  Trecho literal com mais de três linhas, automaticamente formatado com recuo de
  4 cm à esquerda, fonte tamanho 10 e espaçamento simples (Autor, 2026, p. 15).
\end{CitacaoLonga}
```

### 5. Caixa de Ferramentas no Final do Arquivo
Na **PARTE 6** do `modelo.tex`, você encontra blocos comentados prontos para copiar e colar (equações com legenda de variáveis, modelos de referências ABNT para artigos, livros, capítulos, leis e teses, apêndices e anexos).
