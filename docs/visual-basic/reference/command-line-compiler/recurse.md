---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a><span data-ttu-id="0219f-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="0219f-102">/recurse</span></span>
<span data-ttu-id="0219f-103">Zkompiluje soubory zdrojového kódu ve všech zadaný adresář nebo adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0219f-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0219f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0219f-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0219f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0219f-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="0219f-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0219f-106">Optional.</span></span> <span data-ttu-id="0219f-107">Adresář, ve kterém chcete vyhledávání začít.</span><span class="sxs-lookup"><span data-stu-id="0219f-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="0219f-108">Pokud není zadaný, začne vyhledávání v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0219f-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="0219f-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0219f-109">Required.</span></span> <span data-ttu-id="0219f-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0219f-110">The file(s) to search for.</span></span> <span data-ttu-id="0219f-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0219f-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0219f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0219f-112">Remarks</span></span>  
 <span data-ttu-id="0219f-113">Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití `/recurse`.</span><span class="sxs-lookup"><span data-stu-id="0219f-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="0219f-114">Pokud není zadán žádný název výstupního souboru, kompilátor základny název výstupního souboru na první vstupní soubor zpracovat.</span><span class="sxs-lookup"><span data-stu-id="0219f-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="0219f-115">Obvykle se jedná o první soubor v seznamu souborů kompilovat při zobrazení podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="0219f-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="0219f-116">Z tohoto důvodu je nejlepší určit soubor výstupu pomocí `/out` možnost.</span><span class="sxs-lookup"><span data-stu-id="0219f-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0219f-117">`/recurse` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0219f-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0219f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0219f-118">Example</span></span>  
 <span data-ttu-id="0219f-119">Následující kód zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="0219f-119">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="0219f-120">Následující kód zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory `Test\ABC` adresář a všechny adresáře níže a poté generuje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="0219f-120">The following code compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0219f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0219f-121">See Also</span></span>  
 [<span data-ttu-id="0219f-122">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0219f-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0219f-123">/ out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0219f-123">/out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="0219f-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0219f-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
