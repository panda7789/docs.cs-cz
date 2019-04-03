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
ms.openlocfilehash: 0771ed41d6c58ce7cc98435b405f5819e45393db
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824298"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="50366-102">Příkazové řádky ukázkové kompilace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50366-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="50366-103">Jako alternativu ke kompilaci programů jazyka Visual Basic v sadě Visual Studio můžete zkompilovat z příkazového řádku k vytvoření souborů spustitelný soubor (.exe) nebo dynamická knihovna (.dll).</span><span class="sxs-lookup"><span data-stu-id="50366-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="50366-104">Kompilátor příkazového řádku jazyka Visual Basic podporuje kompletní sadu možností, které řídí vstup a výstup souborů, sestavení a ladění a možnosti preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="50366-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="50366-105">Každá možnost je k dispozici ve dvou formách zaměnitelné: `-option` a `/option`.</span><span class="sxs-lookup"><span data-stu-id="50366-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="50366-106">Tato dokumentace se zobrazí pouze `-option` formuláře.</span><span class="sxs-lookup"><span data-stu-id="50366-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="50366-107">Následující tabulka uvádí některé ukázkové příkazové řádky, které můžete upravit pro vlastní použití.</span><span class="sxs-lookup"><span data-stu-id="50366-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="50366-108">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="50366-108">To</span></span>|<span data-ttu-id="50366-109">Použití</span><span class="sxs-lookup"><span data-stu-id="50366-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="50366-110">Kompilace File.vb a vytvořit File.exe</span><span class="sxs-lookup"><span data-stu-id="50366-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="50366-111">Kompilace File.vb a vytvořit soubor.dll</span><span class="sxs-lookup"><span data-stu-id="50366-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="50366-112">Kompilace File.vb a vytvořit My.exe</span><span class="sxs-lookup"><span data-stu-id="50366-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="50366-113">Kompilace File.vb a vytvořit knihovnu a odkaz na sestavení s názvem soubor.dll</span><span class="sxs-lookup"><span data-stu-id="50366-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="50366-114">Zkompilovat všechny soubory jazyka Visual Basic v aktuálním adresáři s optimalizací na a `DEBUG` symbol definovaný, vytváření File2.exe</span><span class="sxs-lookup"><span data-stu-id="50366-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="50366-115">Zkompilovat všechny soubory jazyka Visual Basic do aktuálního adresáře, vytváření verzí ladění File2.dll pro ladění bez zobrazení loga nebo upozornění</span><span class="sxs-lookup"><span data-stu-id="50366-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="50366-116">Zkompilovat všechny soubory jazyka Visual Basic v aktuálním adresáři Something.dll</span><span class="sxs-lookup"><span data-stu-id="50366-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="50366-117">Při vytváření projektu pomocí rozhraní IDE sady Visual Studio můžete zobrazit informace o přidružené **Vbc –** příkaz s jeho možnosti kompilátoru v okně výstup.</span><span class="sxs-lookup"><span data-stu-id="50366-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="50366-118">Chcete-li zobrazit tyto informace, otevřete [dialogové okno Možnosti, projekty a řešení, sestavení a spuštění](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)a pak nastavte **podrobnosti výstupu sestavení projektu nástroje MSBuild** k **normální** nebo vyšší úroveň podrobností.</span><span class="sxs-lookup"><span data-stu-id="50366-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="50366-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50366-119">See also</span></span>

- [<span data-ttu-id="50366-120">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="50366-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="50366-121">Podmíněná kompilace</span><span class="sxs-lookup"><span data-stu-id="50366-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
