---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: fc8dfe41ea56531ff34cd5e551ef24d636227e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400497"
---
# <a name="-recurse"></a><span data-ttu-id="ff760-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="ff760-102">-recurse</span></span>
<span data-ttu-id="ff760-103">Zkompiluje soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře, nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="ff760-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff760-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff760-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ff760-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ff760-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="ff760-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ff760-106">Optional.</span></span> <span data-ttu-id="ff760-107">Adresář, ve kterém chcete zahájit hledání.</span><span class="sxs-lookup"><span data-stu-id="ff760-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="ff760-108">Pokud není zadán, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="ff760-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="ff760-109">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ff760-109">Required.</span></span> <span data-ttu-id="ff760-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="ff760-110">The file(s) to search for.</span></span> <span data-ttu-id="ff760-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="ff760-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff760-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff760-112">Remarks</span></span>  
 <span data-ttu-id="ff760-113">Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez použití `-recurse` .</span><span class="sxs-lookup"><span data-stu-id="ff760-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="ff760-114">Pokud není zadán žádný název výstupního souboru, kompilátor vyloží název výstupního souboru v prvním zpracovávaném vstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="ff760-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="ff760-115">Většinou se jedná o první soubor v seznamu souborů kompilovaných při abecedním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ff760-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="ff760-116">Z tohoto důvodu je nejlepší zadat výstupní soubor pomocí `-out` Možnosti.</span><span class="sxs-lookup"><span data-stu-id="ff760-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff760-117">Tato `-recurse` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ff760-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff760-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff760-118">Example</span></span>  
 <span data-ttu-id="ff760-119">Následující příkaz zkompiluje všechny Visual Basic soubory v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="ff760-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="ff760-120">Následující příkaz zkompiluje všechny Visual Basic soubory v `Test\ABC` adresáři a všech adresářích pod ním a pak vygeneruje `Test.ABC.dll` .</span><span class="sxs-lookup"><span data-stu-id="ff760-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff760-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff760-121">See also</span></span>

- [<span data-ttu-id="ff760-122">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ff760-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ff760-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff760-123">-out (Visual Basic)</span></span>](out.md)
- [<span data-ttu-id="ff760-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ff760-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
