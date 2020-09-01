---
description: -rekurze (možnosti kompilátoru C#)
title: -rekurze (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: 3edd7e23358bc0569dae6204d519209df1ade290
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124822"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="beef6-103">-rekurze (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="beef6-103">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="beef6-104">Možnost-rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (dir), nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="beef6-104">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beef6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="beef6-105">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="beef6-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="beef6-106">Arguments</span></span>  
 <span data-ttu-id="beef6-107">`dir` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="beef6-107">`dir` (optional)</span></span>  
 <span data-ttu-id="beef6-108">Adresář, ve kterém chcete zahájit hledání.</span><span class="sxs-lookup"><span data-stu-id="beef6-108">The directory in which you want the search to begin.</span></span> <span data-ttu-id="beef6-109">Pokud tento parametr nezadáte, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="beef6-109">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="beef6-110">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="beef6-110">The file(s) to search for.</span></span> <span data-ttu-id="beef6-111">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="beef6-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="beef6-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="beef6-112">Remarks</span></span>  
 <span data-ttu-id="beef6-113">Možnost **-rekurze** umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře ( `dir` ), nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="beef6-113">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="beef6-114">Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bez použití **rekurze**.</span><span class="sxs-lookup"><span data-stu-id="beef6-114">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="beef6-115">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="beef6-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beef6-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="beef6-116">Example</span></span>  
 <span data-ttu-id="beef6-117">Zkompiluje všechny soubory v jazyce C# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="beef6-117">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="beef6-118">Zkompiluje všechny soubory v jazyce C# v adresáři dir1\dir2 a všech adresářích pod ním a vygeneruje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="beef6-118">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="beef6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="beef6-119">See also</span></span>

- [<span data-ttu-id="beef6-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="beef6-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="beef6-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="beef6-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
