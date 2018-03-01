---
title: "-recurse (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b50454112bc7aee6c3e0f8fe674e8727ca9e49be
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="ec50d-102">-recurse (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ec50d-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="ec50d-103">-Recurse – možnost umožňuje kompilovat soubory zdrojového kódu ve všech zadaný adresář (dir) nebo adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="ec50d-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec50d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec50d-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec50d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ec50d-105">Arguments</span></span>  
 <span data-ttu-id="ec50d-106">`dir`(volitelné)</span><span class="sxs-lookup"><span data-stu-id="ec50d-106">`dir` (optional)</span></span>  
 <span data-ttu-id="ec50d-107">Adresář, ve kterém chcete vyhledávání začít.</span><span class="sxs-lookup"><span data-stu-id="ec50d-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="ec50d-108">Pokud není tento parametr zadán, začne vyhledávání v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="ec50d-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="ec50d-109">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="ec50d-109">The file(s) to search for.</span></span> <span data-ttu-id="ec50d-110">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="ec50d-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec50d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec50d-111">Remarks</span></span>  
 <span data-ttu-id="ec50d-112">**-Recurse** možnost umožňuje zkompilovat soubory zdrojového kódu ve všech zadaného adresáře (`dir`) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="ec50d-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="ec50d-113">Můžete použít zástupné znaky v názvu souboru pro kompilaci všechny odpovídající soubory v adresáři projektu bez použití **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="ec50d-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="ec50d-114">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="ec50d-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec50d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec50d-115">Example</span></span>  
 <span data-ttu-id="ec50d-116">Kompiluje všechny soubory C# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="ec50d-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="ec50d-117">Kompiluje všechny soubory C# v adresáři dir1\dir2 a všech adresářích pod ním a generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="ec50d-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec50d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec50d-118">See Also</span></span>  
 [<span data-ttu-id="ec50d-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ec50d-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ec50d-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ec50d-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
