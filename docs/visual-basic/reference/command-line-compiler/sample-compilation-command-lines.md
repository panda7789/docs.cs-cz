---
title: Příkazové řádky ukázkové kompilace (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0f1fc1d269801efdbf2e89d10679dc8159851f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653660"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="0e862-102">Příkazové řádky ukázkové kompilace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e862-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="0e862-103">Jako alternativu k kompilace jazyka Visual Basic programů z v sadě Visual Studio můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="0e862-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="0e862-104">Visual Basic – kompilátor příkazového řádku podporuje úplnou sadu možností, které řídí vstup a výstup souborů, sestavení a ladění a preprocesoru možnosti.</span><span class="sxs-lookup"><span data-stu-id="0e862-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="0e862-105">Každá možnost je k dispozici ve dvou formách zaměňovat: `-option` a `/option`.</span><span class="sxs-lookup"><span data-stu-id="0e862-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="0e862-106">Tato dokumentace se zobrazí pouze `-option` formuláře.</span><span class="sxs-lookup"><span data-stu-id="0e862-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="0e862-107">Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="0e862-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="0e862-108">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="0e862-108">To</span></span>|<span data-ttu-id="0e862-109">Použití</span><span class="sxs-lookup"><span data-stu-id="0e862-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="0e862-110">Kompilace File.vb a vytvořit File.exe</span><span class="sxs-lookup"><span data-stu-id="0e862-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="0e862-111">Kompilace File.vb a vytvoření souboru File.dll</span><span class="sxs-lookup"><span data-stu-id="0e862-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="0e862-112">Kompilace File.vb a vytvořit My.exe</span><span class="sxs-lookup"><span data-stu-id="0e862-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="0e862-113">Kompilace File.vb a vytvořte knihovnu a referenční sestavení s názvem souboru File.dll</span><span class="sxs-lookup"><span data-stu-id="0e862-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="0e862-114">Kompilaci všech souborů jazyka Visual Basic v aktuálním adresáři, s optimalizací na a `DEBUG` symbol definované, který vytvořil File2.exe</span><span class="sxs-lookup"><span data-stu-id="0e862-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="0e862-115">Kompilaci všech souborů jazyka Visual Basic v aktuálním adresáři, který vytvořil ladicí verze File2.dll pro ladění bez zobrazování logo nebo upozornění</span><span class="sxs-lookup"><span data-stu-id="0e862-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="0e862-116">Všechny soubory jazyka Visual Basic v aktuálním adresáři na Something.dll kompilace</span><span class="sxs-lookup"><span data-stu-id="0e862-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="0e862-117">Při sestavování projektu pomocí prostředí Visual Studio IDE, můžete zobrazit informace o přidruženého **Vbc –** s jeho – možnosti kompilátoru v okně výstupu.</span><span class="sxs-lookup"><span data-stu-id="0e862-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="0e862-118">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a poté nastavte **výstup sestavení projektu MSBuild podrobností** k **normální** nebo vyšší úrovni podrobností.</span><span class="sxs-lookup"><span data-stu-id="0e862-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="0e862-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e862-119">See Also</span></span>  
 [<span data-ttu-id="0e862-120">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0e862-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0e862-121">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="0e862-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
