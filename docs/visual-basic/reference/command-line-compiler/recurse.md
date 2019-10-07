---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005262"
---
# <a name="-recurse"></a><span data-ttu-id="fb323-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="fb323-102">-recurse</span></span>
<span data-ttu-id="fb323-103">Zkompiluje soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře, nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="fb323-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb323-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb323-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb323-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fb323-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="fb323-106">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fb323-106">Optional.</span></span> <span data-ttu-id="fb323-107">Adresář, ve kterém chcete zahájit hledání.</span><span class="sxs-lookup"><span data-stu-id="fb323-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="fb323-108">Pokud není zadán, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="fb323-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="fb323-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="fb323-109">Required.</span></span> <span data-ttu-id="fb323-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="fb323-110">The file(s) to search for.</span></span> <span data-ttu-id="fb323-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="fb323-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb323-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb323-112">Remarks</span></span>  
 <span data-ttu-id="fb323-113">Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez použití `-recurse`.</span><span class="sxs-lookup"><span data-stu-id="fb323-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="fb323-114">Pokud není zadán žádný název výstupního souboru, kompilátor vyloží název výstupního souboru v prvním zpracovávaném vstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="fb323-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="fb323-115">Většinou se jedná o první soubor v seznamu souborů kompilovaných při abecedním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fb323-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="fb323-116">Z tohoto důvodu je nejlepší zadat výstupní soubor pomocí možnosti `-out`.</span><span class="sxs-lookup"><span data-stu-id="fb323-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb323-117">Možnost `-recurse` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="fb323-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb323-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb323-118">Example</span></span>  
 <span data-ttu-id="fb323-119">Následující příkaz zkompiluje všechny Visual Basic soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="fb323-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="fb323-120">Následující příkaz zkompiluje všechny Visual Basic soubory v adresáři `Test\ABC` a všech adresářích pod ním a pak vygeneruje `Test.ABC.dll`.</span><span class="sxs-lookup"><span data-stu-id="fb323-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb323-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb323-121">See also</span></span>

- [<span data-ttu-id="fb323-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="fb323-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="fb323-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb323-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="fb323-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="fb323-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
