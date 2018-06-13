---
title: -recurse (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 7d18fb2b1710e074653e054d003be762d947d1be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214586"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="0898d-102">-recurse (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0898d-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="0898d-103">-Recurse – možnost umožňuje kompilovat soubory zdrojového kódu ve všech zadaný adresář (dir) nebo adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0898d-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0898d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0898d-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0898d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0898d-105">Arguments</span></span>  
 <span data-ttu-id="0898d-106">`dir` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0898d-106">`dir` (optional)</span></span>  
 <span data-ttu-id="0898d-107">Adresář, ve kterém chcete vyhledávání začít.</span><span class="sxs-lookup"><span data-stu-id="0898d-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="0898d-108">Pokud není tento parametr zadán, začne vyhledávání v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0898d-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="0898d-109">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0898d-109">The file(s) to search for.</span></span> <span data-ttu-id="0898d-110">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0898d-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0898d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0898d-111">Remarks</span></span>  
 <span data-ttu-id="0898d-112">**-Recurse** možnost umožňuje zkompilovat soubory zdrojového kódu ve všech zadaného adresáře (`dir`) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="0898d-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="0898d-113">Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="0898d-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="0898d-114">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="0898d-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0898d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0898d-115">Example</span></span>  
 <span data-ttu-id="0898d-116">Kompiluje všechny soubory C# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0898d-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="0898d-117">Kompiluje všechny soubory C# v adresáři dir1\dir2 a všech adresářích pod ním a generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="0898d-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0898d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0898d-118">See Also</span></span>  
 [<span data-ttu-id="0898d-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0898d-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="0898d-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0898d-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
