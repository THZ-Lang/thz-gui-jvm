# thz-gui — Desktop IDE Swing FlatLaf do THZ-LANG (Java 25)

Ambiente integrado de desenvolvimento (IDE) desktop para a linguagem THZ-LANG, construído com FlatLaf (temas Dark/Light), realce léxico e semântico em tempo real, editor estruturado, gutter ancorado e motor reativo de formulários visuais. Consome diretamente o núcleo [`thz-core-jvm`](../thz-core-jvm).

---

## 🌟 Recursos Principais

- **Editor Avançado & Syntax Highlighting:** Realce de sintaxe em tempo real para as sintaxes canônica e dual moderna (`{ ... }`, `fn`, `struct`, `var`, `val`), marcadores de erro precisos `[Linha L:C]` e recuo inteligente.
- **Gutter Interativo:** Numeração ancorada, marcadores de dobradura de código (*code folding*) e pontos de interrupção (breakpoints) integrados ao DAP.
- **Barras Modulares e Ações Rápidas:** Menus de arquivo, ferramentas, seletor de dialeto e barra de status com monitor de runtime e métricas de desempenho.
- **Executor Assíncrono:** Execução não-bloqueante fora da Event Dispatch Thread (EDT) para checagens (`check`), execução (`run`), formatação (`fmt`), auditoria (`audit`), documentação viva (`docgen`) e inspeção de IR.
- **Formulários Declarativos Reativos:** Renderização instantânea de componentes de interface gráfica a partir do subsistema `TELA` e arquivos `.thzui`.
- **Configuração & JVMs:** Detecção automática de JDKs instalados, histórico de arquivos recentes e persistência em `~/.thz/desktop-config.json`.

---

## 🚀 Execução e Build

```bash
# Execução de testes automatizados
./gradlew :thz-gui-jvm:test

# Iniciar a Desktop IDE a partir da raiz
./gradlew gui

# Ou via scripts de inicialização
./scripts/gui.sh          # Linux / macOS
.\scripts\gui.ps1        # Windows
```

---

## ⚡ Compilação Nativa AOT (GraalVM)

O `thz-gui-jvm` é configurado com *reachability metadata* e Look & Feel nativo para viabilizar compilação AOT sob o GraalVM:

```powershell
./gradlew :thz-gui-jvm:nativeCompile
```

Gera o binário nativo `thz-desktop.exe` com inicialização instantânea (< 15ms).

> [!NOTE]
> Se houver mudanças na interface gráfica que exijam novos metadados de reflexão ou JNI, execute a coleta automatizada:
> ```powershell
> ./gradlew :thz-gui-jvm:guiColetarMetadadosAgente
> ```

---

## 📦 Dependência do Core

```kotlin
implementation("thz.lang:thz-core:0.4.0")
```
Resolvido via Gradle Composite Build a partir de `../thz-core-jvm`.

---

## 🛠️ Stack Técnica

- **Plataforma:** Java 25 (toolchain)
- **Look and Feel:** FlatLaf 3.5 (Dark & Light)
- **Framework UI:** Java Swing / AWT
- **Testes:** JUnit 5.11
- **Compilador AOT:** GraalVM Native Image
- **Build System:** Gradle (Kotlin DSL)
