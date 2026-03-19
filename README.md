# 🧮 Calculadora BPC/LOAS — Avaliação Biopsicossocial

Ferramenta de apoio para calcular o resultado da avaliação biopsicossocial de requerentes do Benefício de Prestação Continuada (BPC/LOAS), com base na **Portaria Conjunta MDS/INSS nº 2/2015**.

> ⚠️ **Ferramenta de apoio.** Não substitui análise jurídica, médica ou pericial. O resultado deve ser interpretado no contexto do caso concreto.

---

## ✨ Funcionalidades

- **Cálculo automático** dos três componentes (Fatores Ambientais, Atividades e Participação, Funções do Corpo)
- **Todos os quesitos** da Portaria 2/2015 com pontuação individual (0–4)
- **Tabela Conclusiva (Anexo IV)** aplicada automaticamente — resultado em tempo real
- **Importação do PDF do INSS** — cole o texto copiado e os campos são preenchidos automaticamente
- **Majoração de Funções do Corpo** (Estrutura > Função e Prognóstico Desfavorável — art. 7º)
- **Minuta automática** de fundamentação, pronta para copiar
- **Funciona offline** — arquivo HTML autossuficiente, sem servidor, sem instalação

---

## 📋 Base normativa

| Documento | Referência |
|---|---|
| Portaria Conjunta MDS/INSS nº 2/2015 | Critérios, procedimentos e instrumentos de avaliação |
| Lei nº 8.742/1993 (LOAS) | Art. 20, §§ 2º e 10 — definição de pessoa com deficiência |
| Decreto nº 6.214/2007 | Regulamentação do BPC |
| Convenção ONU sobre Direitos da PcD | Decreto Legislativo nº 186/2008 |
| CIF — Classificação Internacional de Funcionalidade | OMS / Resolução WHA 54.21 |

---

## 🚀 Como usar

### 1. Abrir a calculadora

Baixe o arquivo `calculadora-bpc.html` e abra no navegador (Chrome, Firefox, Edge ou Safari). Não é necessário instalar nada.

### 2. Configurações iniciais

- Selecione a **faixa etária** do avaliado (16 anos ou mais / menor de 16 anos)
- Se as alterações forem **resolvíveis em menos de 2 anos**, ative o toggle — o benefício é indeferido imediatamente (art. 8º, III)

### 3. Preencher os domínios

Clique no **nome de cada domínio** para abrir o painel de quesitos.

**Duas formas de pontuar:**

| Forma | Como funciona |
|---|---|
| **Quesitos individuais (0–4)** | Clique no número de cada quesito. O qualificador do domínio é calculado automaticamente pela média. |
| **Qualificador direto (N/L/M/G/C)** | Use os botões no cabeçalho do domínio para definir manualmente. Aparece indicação em roxo. Clique em "✕ Limpar manual" para voltar ao cálculo automático. |

### 4. Majorações de Funções do Corpo

O qualificador de Funções do Corpo pode ser majorado em um nível (não cumulativo) em dois casos:

- **Estrutura do Corpo > Função** — alterações estruturais mais graves que as funcionais
- **Prognóstico Desfavorável** — quadro progressivo, degenerativo ou irreversível

Ative os toggles correspondentes no painel de Funções do Corpo.

### 5. Importar PDF do INSS

O painel **"Importar texto da Avaliação INSS"** preenche os campos automaticamente:

1. Abra o PDF da avaliação biopsicossocial (Espécie B87) no seu leitor de PDF
2. Pressione `Ctrl+A` para selecionar tudo, depois `Ctrl+C` para copiar
3. Na calculadora, clique em **▾ Abrir** no painel dourado
4. Cole o texto (`Ctrl+V`) na área de texto
5. Clique em **⚡ Analisar e preencher**

> ⚠️ Funciona apenas com **PDFs digitais nativos** do sistema do INSS. PDFs digitalizados por scanner não contêm texto extraível.

### 6. Ver o resultado

O painel lateral atualiza em tempo real com:

- Qualificadores finais dos três componentes
- Veredicto **Deferido ✓** ou **Indeferido ✗** com base na Tabela Conclusiva
- Combinação exata (FA × AP × FC) que levou ao resultado

### 7. Gerar a minuta

Clique em **"Gerar texto"** no painel de Minuta para obter um texto padronizado de fundamentação, pronto para copiar e colar na decisão ou petição.

---

## 📊 Escala de qualificadores (CIF)

| Código | Letra | Faixa | Significado |
|---|---|---|---|
| 0 | **N** | 0 – 4% | Nenhuma |
| 1 | **L** | 5 – 24% | Leve |
| 2 | **M** | 25 – 49% | Moderada |
| 3 | **G** | 50 – 95% | Grave |
| 4 | **C** | 96 – 100% | Completa |

---

## 🔢 Componentes e fórmulas de cálculo

### Fatores Ambientais (e1–e5) — Avaliação Social

```
FA = [(e1 + e2 + e3 + e4 + e5) × 5] − 0,1
```

Domínios: Produtos e Tecnologia (e1) · Habitabilidade (e2) · Apoio e Relacionamentos (e3) · Atitudes (e4) · Serviços, Sistemas e Políticas (e5)

### Atividades e Participação (d1–d9) — Avaliação Mista

```
AP = [(d1 + d2 + d3 + d4 + d5 + d6 + d7 + d8 + d9) × 2,7778] − 0,1
```

| Domínios | Responsável |
|---|---|
| d1 Aprendizagem · d2 Tarefas · d3 Comunicação · d4 Mobilidade · d5 Cuidado Pessoal | 🩺 Perito Médico |
| d6 Vida Doméstica · d7 Relações Interpessoais · d8 Áreas Principais da Vida · d9 Vida Comunitária | 👥 Assistente Social |

### Funções do Corpo (b1–b8) — Avaliação Médica

```
FC = maior qualificador entre b1 e b8 (com possível majoração de um nível)
```

Domínios: Mental (b1) · Sensoriais (b2) · Voz e Fala (b3) · Cardiovascular/Hemato/Imuno/Resp. (b4) · Digestivo/Metabólico (b5) · Geniturinário (b6) · Neuromusculoesquelético (b7) · Pele (b8)

---

## ✅ Regras da Tabela Conclusiva (Anexo IV)

**Indeferimento imediato quando:**
- FC = N ou L (independentemente dos demais)
- AP = N ou L (independentemente dos demais)
- Alterações resolvíveis em menos de 2 anos (art. 8º, III)

**Deferimento quando:**
- FC ≥ M **e** AP ≥ M — exceto M×M, que exige FA ≥ G
- Qualquer combinação com FC ≥ G ou AP ≥ G (quando o outro também é ≥ M)

---

## ❓ Perguntas frequentes

**Preciso preencher todos os quesitos?**
Não. A calculadora funciona com qualificadores diretos (N/L/M/G/C) por domínio. O preenchimento por quesito é opcional e aumenta a fidelidade à metodologia.

**Os dados ficam salvos?**
Não. Os dados existem apenas na sessão atual. Use a minuta para registrar o resultado antes de fechar.

**Funciona em dispositivo móvel?**
Sim, o layout é responsivo.

**Por que o PDF importou apenas parte dos domínios?**
A avaliação biopsicossocial pode estar dividida em dois PDFs (médico e social). Importe cada um separadamente — os campos se acumulam.

---

## 📁 Arquivos

```
calculadora-bpc.html    ← calculadora completa (arquivo único, autossuficiente)
manual_bpc.docx         ← manual do usuário em Word
README.md               ← este arquivo
```

---

## ⚖️ Aviso legal

Esta ferramenta é de **apoio técnico** e não substitui análise jurídica, médica ou pericial. Os resultados devem ser interpretados no contexto do caso concreto, observada a legislação vigente e a jurisprudência aplicável.

---

*Portaria Conjunta MDS/INSS nº 2/2015 · Lei nº 8.742/1993 (LOAS) · Decreto nº 6.214/2007*
