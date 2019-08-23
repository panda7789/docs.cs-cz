---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956268"
---
# <a name="-recurse"></a><span data-ttu-id="acbbf-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="acbbf-102">-recurse</span></span>
<span data-ttu-id="acbbf-103">Zkompiluje soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře, nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="acbbf-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acbbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acbbf-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="acbbf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="acbbf-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="acbbf-106">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="acbbf-106">Optional.</span></span> <span data-ttu-id="acbbf-107">Adresář, ve kterém chcete zahájit hledání.</span><span class="sxs-lookup"><span data-stu-id="acbbf-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="acbbf-108">Pokud není zadán, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="acbbf-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="acbbf-109">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="acbbf-109">Required.</span></span> <span data-ttu-id="acbbf-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="acbbf-110">The file(s) to search for.</span></span> <span data-ttu-id="acbbf-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="acbbf-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acbbf-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acbbf-112">Remarks</span></span>  
 <span data-ttu-id="acbbf-113">Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez `-recurse`použití.</span><span class="sxs-lookup"><span data-stu-id="acbbf-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="acbbf-114">Pokud není zadán žádný název výstupního souboru, kompilátor vyloží název výstupního souboru v prvním zpracovávaném vstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="acbbf-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="acbbf-115">Většinou se jedná o první soubor v seznamu souborů kompilovaných při abecedním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="acbbf-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="acbbf-116">Z tohoto důvodu je nejlepší zadat výstupní soubor pomocí `-out` možnosti.</span><span class="sxs-lookup"><span data-stu-id="acbbf-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acbbf-117">Tato `-recurse` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="acbbf-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acbbf-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="acbbf-118">Example</span></span>  
 <span data-ttu-id="acbbf-119">Následující příkaz zkompiluje všechny Visual Basic soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="acbbf-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="acbbf-120">Následující příkaz zkompiluje všechny Visual Basic soubory v `Test\ABC` adresáři a všech adresářích pod ním a pak vygeneruje. `Test.ABC.dll`</span><span class="sxs-lookup"><span data-stu-id="acbbf-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="acbbf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acbbf-121">See also</span></span>

- [<span data-ttu-id="acbbf-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="acbbf-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="acbbf-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acbbf-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="acbbf-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="acbbf-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
