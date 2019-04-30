---
title: Sestavení z příkazového řádku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 798baa90308c83e42b335635fb23a9983f5180fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61839381"
---
# <a name="building-from-the-command-line-visual-basic"></a>Sestavení z příkazového řádku (Visual Basic)
Projekt jazyka Visual Basic tvoří jeden nebo více samostatných zdrojových souborů. Během procesu označované jako kompilace, tyto soubory jsou svedla dohromady do jednoho balíčku – jeden spustitelný soubor, který může běžet jako aplikace.  
  
 Visual Basic poskytuje kompilátoru příkazového řádku jako alternativu ke kompilaci programů z v rámci integrovaného vývojového prostředí (IDE) sady Visual Studio. Kompilátoru příkazového řádku je navržené pro situace, ve kterých nechcete, aby úplná sada funkcí v rozhraní IDE – třeba když používáte nebo zápis pro počítače s omezené systémové paměti nebo prostor úložiště.  
  
  Chcete-li zkompilovat zdrojové soubory z integrovaného vývojového prostředí Visual Studio, zvolte **sestavení** z **sestavení** nabídky.  
  
> [!TIP]
>  Při sestavování projektu soubory pomocí rozhraní IDE sady Visual Studio můžete zobrazit informace o přidružené **Vbc –** příkazu a jeho přepínače v okně výstup. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **podrobnosti výstupu sestavení projektu nástroje MSBuild** k **normální** nebo vyšší úroveň podrobností. Další informace najdete v tématu [jak: Zobrazování, ukládání a konfigurace souborů protokolu sestavení](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).  
  
 Soubory projektu (.vbproj) z příkazového řádku můžete zkompilovat pomocí nástroje MSBuild. Další informace najdete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [názorný postup: Použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání kompilátoru příkazového řádku](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Popisuje postup volání kompilátoru příkazového řádku do příkazového řádku nebo z konkrétního podadresáře.  
  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Obsahuje seznam ukázkové příkazové řádky, které můžete upravit pro vlastní použití.  
  
## <a name="related-sections"></a>Související oddíly  
 [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 Poskytuje seznam – možnosti kompilátoru, uspořádány podle abecedy nebo podle účelu.  
  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Popisuje, jak sestavit konkrétní části kódu.  
  
 [Sestavování a čištění projektů a řešení v sadě Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Popisuje, jak uspořádat co bude součástí jiné sestavení, zvolte Vlastnosti projektu a ujistěte se, že je ve správném pořadí sestavení projektů.
