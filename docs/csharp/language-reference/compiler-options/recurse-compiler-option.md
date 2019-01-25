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
ms.openlocfilehash: a4a55090cf465d0eac05303392ba7500dd96ee90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679367"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="e6d40-102">-recurse (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e6d40-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="e6d40-103">-Recurse – možnost umožňuje kompilaci souborů zdrojového kódu ve všech adresářích podřízené zadaný adresář (adresář) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="e6d40-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d40-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6d40-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e6d40-105">Arguments</span></span>  
 <span data-ttu-id="e6d40-106">`dir` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="e6d40-106">`dir` (optional)</span></span>  
 <span data-ttu-id="e6d40-107">Adresář, ve kterém chcete, aby hledání začalo.</span><span class="sxs-lookup"><span data-stu-id="e6d40-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="e6d40-108">Pokud není zadaný, hledání začne v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="e6d40-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="e6d40-109">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="e6d40-109">The file(s) to search for.</span></span> <span data-ttu-id="e6d40-110">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="e6d40-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6d40-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6d40-111">Remarks</span></span>  
 <span data-ttu-id="e6d40-112">**-Recurse** možnost umožňuje kompilaci souborů zdrojového kódu ve všech adresářích podřízené zadaného adresáře (`dir`) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="e6d40-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="e6d40-113">Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="e6d40-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="e6d40-114">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="e6d40-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6d40-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6d40-115">Example</span></span>  
 <span data-ttu-id="e6d40-116">Kompiluje všechny soubory jazyka C# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="e6d40-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="e6d40-117">Kompiluje se všechny soubory jazyka C# v adresáři dir1\dir2 a všechny adresáře pod ní a generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="e6d40-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6d40-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6d40-118">See also</span></span>

- [<span data-ttu-id="e6d40-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6d40-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="e6d40-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e6d40-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
