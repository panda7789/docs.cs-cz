---
title: Sestavení z příkazového řádku (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1fd4054838925267647986a5166fd88037b17fae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="building-from-the-command-line-visual-basic"></a>Sestavení z příkazového řádku (Visual Basic)
Projektu jazyka Visual Basic se skládá z jedné nebo více samostatných zdrojové soubory. Během procesu říká kompilace, tyto soubory jsou shromážděna do jednoho balíčku – jeden spustitelný soubor, který může běžet jako aplikace.  
  
 Visual Basic poskytuje jako alternativu k kompilace programů v nástroji příkazového řádku kompilátoru [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Kompilátor příkazového řádku je navržené pro situace, ve kterých nechcete, aby úplnou sadu funkcí v prostředí IDE – například když používáte nebo zápis pro počítače s omezené systémové paměti nebo úložný prostor.  
  
  Zkompilovat zdrojové soubory v rámci [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] integrovaného vývojového prostředí, vyberte **sestavení** příkaz **sestavení** nabídky.  
  
> [!TIP]
>  Při sestavování projektu soubory pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** příkazu a jeho přepínače v okně výstupu. Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností. Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
 Soubory projektu (.vbproj) na příkazovém řádku můžete zkompilovat pomocí nástroje MSBuild. Další informace najdete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [návod: použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Volání kompilátoru příkazového řádku](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Popisuje, jak má být vyvolán kompilátoru příkazového řádku do příkazového řádku nebo z určité podadresáři.  
  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Poskytuje seznam příkazové řádky ukázkové, které lze upravit pro vlastní použití.  
  
## <a name="related-sections"></a>Související oddíly  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 Poskytuje seznam – možnosti kompilátoru, uspořádané podle abecedy nebo účel.  
  
 [Podmíněná kompilace](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Popisuje, jak zkompilovat určité části kódu.  
  
 [Sestavování a čištění projektů a řešení v sadě Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Popisuje, jak uspořádat co budou zahrnuty do různých sestavení, vyberte vlastnosti projektu a ujistěte se, že sestavení projektů ve správném pořadí.
