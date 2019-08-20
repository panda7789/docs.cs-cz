---
title: -rekurzeC# (možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606751"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="c1afd-102">-rekurzeC# (možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="c1afd-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="c1afd-103">Možnost-rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (dir), nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="c1afd-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1afd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1afd-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1afd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c1afd-105">Arguments</span></span>  
 <span data-ttu-id="c1afd-106">`dir`volitelné</span><span class="sxs-lookup"><span data-stu-id="c1afd-106">`dir` (optional)</span></span>  
 <span data-ttu-id="c1afd-107">Adresář, ve kterém chcete zahájit hledání.</span><span class="sxs-lookup"><span data-stu-id="c1afd-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="c1afd-108">Pokud tento parametr nezadáte, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="c1afd-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="c1afd-109">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c1afd-109">The file(s) to search for.</span></span> <span data-ttu-id="c1afd-110">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="c1afd-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1afd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1afd-111">Remarks</span></span>  
 <span data-ttu-id="c1afd-112">Možnost **-** rekurze umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích buď určeného adresáře (`dir`), nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="c1afd-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="c1afd-113">Můžete použít zástupné znaky v názvu souboru k zkompilování všech vyhovujících souborů v adresáři projektu bezpoužití rekurze.</span><span class="sxs-lookup"><span data-stu-id="c1afd-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="c1afd-114">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="c1afd-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1afd-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1afd-115">Example</span></span>  
 <span data-ttu-id="c1afd-116">Zkompiluje všechny C# soubory v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="c1afd-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="c1afd-117">Zkompiluje všechny C# soubory v adresáři dir1\dir2 a všech adresářích pod ním a vygeneruje dir2. dll:</span><span class="sxs-lookup"><span data-stu-id="c1afd-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1afd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1afd-118">See also</span></span>

- [<span data-ttu-id="c1afd-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c1afd-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c1afd-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="c1afd-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
