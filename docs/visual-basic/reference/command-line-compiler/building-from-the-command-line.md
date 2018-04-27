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
ms.openlocfilehash: 9a9dee47f06e4f7d9fc8d237376df7707130921d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="cf465-102">Sestavení z příkazového řádku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf465-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="cf465-103">Projektu jazyka Visual Basic se skládá z jedné nebo více samostatných zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="cf465-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="cf465-104">Během procesu říká kompilace, tyto soubory jsou shromážděna do jednoho balíčku – jeden spustitelný soubor, který může běžet jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="cf465-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="cf465-105">Visual Basic poskytuje kompilátoru příkazového řádku jako alternativu k kompilace programů z v sadě Visual Studio integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="cf465-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="cf465-106">Kompilátor příkazového řádku je navržené pro situace, ve kterých nechcete, aby úplnou sadu funkcí v prostředí IDE – například když používáte nebo zápis pro počítače s omezené systémové paměti nebo úložný prostor.</span><span class="sxs-lookup"><span data-stu-id="cf465-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="cf465-107">Kompilace zdrojové soubory z v prostředí Visual Studio IDE, vyberte **sestavení** příkaz **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cf465-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="cf465-108">Při sestavování projektu soubory pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** příkazu a jeho přepínače v okně výstupu.</span><span class="sxs-lookup"><span data-stu-id="cf465-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="cf465-109">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností.</span><span class="sxs-lookup"><span data-stu-id="cf465-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="cf465-110">Další informace najdete v tématu [postupy: zobrazení, ukládání a konfigurace souborů protokolu sestavení](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="cf465-110">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="cf465-111">Soubory projektu (.vbproj) na příkazovém řádku můžete zkompilovat pomocí nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="cf465-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="cf465-112">Další informace najdete v tématu [Reference k příkazovému řádku](/visualstudio/msbuild/msbuild-command-line-reference) a [návod: použití nástroje MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="cf465-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf465-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cf465-113">In This Section</span></span>  
 [<span data-ttu-id="cf465-114">Postupy: Volání kompilátoru příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="cf465-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="cf465-115">Popisuje, jak má být vyvolán kompilátoru příkazového řádku do příkazového řádku nebo z určité podadresáři.</span><span class="sxs-lookup"><span data-stu-id="cf465-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="cf465-116">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="cf465-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="cf465-117">Poskytuje seznam příkazové řádky ukázkové, které lze upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="cf465-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cf465-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cf465-118">Related Sections</span></span>  
 [<span data-ttu-id="cf465-119">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="cf465-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="cf465-120">Poskytuje seznam – možnosti kompilátoru, uspořádané podle abecedy nebo účel.</span><span class="sxs-lookup"><span data-stu-id="cf465-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="cf465-121">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="cf465-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="cf465-122">Popisuje, jak zkompilovat určité části kódu.</span><span class="sxs-lookup"><span data-stu-id="cf465-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="cf465-123">Sestavování a čištění projektů a řešení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cf465-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="cf465-124">Popisuje, jak uspořádat co budou zahrnuty do různých sestavení, vyberte vlastnosti projektu a ujistěte se, že sestavení projektů ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf465-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
