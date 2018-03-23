---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-recurse"></a><span data-ttu-id="cebd9-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="cebd9-102">-recurse</span></span>
<span data-ttu-id="cebd9-103">Zkompiluje soubory zdrojového kódu ve všech zadaný adresář nebo adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="cebd9-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cebd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cebd9-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="cebd9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cebd9-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="cebd9-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cebd9-106">Optional.</span></span> <span data-ttu-id="cebd9-107">Adresář, ve kterém chcete vyhledávání začít.</span><span class="sxs-lookup"><span data-stu-id="cebd9-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="cebd9-108">Pokud není zadaný, začne vyhledávání v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="cebd9-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="cebd9-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="cebd9-109">Required.</span></span> <span data-ttu-id="cebd9-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="cebd9-110">The file(s) to search for.</span></span> <span data-ttu-id="cebd9-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="cebd9-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cebd9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cebd9-112">Remarks</span></span>  
 <span data-ttu-id="cebd9-113">Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="cebd9-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="cebd9-114">Pokud není zadán žádný název výstupního souboru, kompilátor základny název výstupního souboru na první vstupní soubor zpracovat.</span><span class="sxs-lookup"><span data-stu-id="cebd9-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="cebd9-115">Obvykle se jedná o první soubor v seznamu souborů kompilovat při zobrazení podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="cebd9-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="cebd9-116">Z tohoto důvodu je nejlepší určit soubor výstupu pomocí `-out` možnost.</span><span class="sxs-lookup"><span data-stu-id="cebd9-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cebd9-117">`-recurse` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cebd9-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cebd9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="cebd9-118">Example</span></span>  
 <span data-ttu-id="cebd9-119">Následující příkaz zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="cebd9-119">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="cebd9-120">Následující příkaz zkompiluje všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] soubory `Test\ABC` adresář a všechny adresáře níže a poté generuje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="cebd9-120">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cebd9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="cebd9-121">See Also</span></span>  
 [<span data-ttu-id="cebd9-122">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="cebd9-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cebd9-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cebd9-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="cebd9-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="cebd9-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
