---
title: -recurse (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /recurse
helpviewer_keywords:
- /recurse compiler option [C#]
- recurse compiler option [C#]
- -recurse compiler option [C#]
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
ms.openlocfilehash: c82e3019e1a1e3ba45a7000312b54b9d7f64a2db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606751"
---
# <a name="-recurse-c-compiler-options"></a><span data-ttu-id="0099a-102">-recurse (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0099a-102">-recurse (C# Compiler Options)</span></span>
<span data-ttu-id="0099a-103">Možnost -recurse umožňuje kompilovat soubory zdrojového kódu ve všech podřízených adresářích zadaného adresáře (dir) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="0099a-103">The -recurse option enables you to compile source code files in all child directories of either the specified directory (dir) or of the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0099a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0099a-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0099a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0099a-105">Arguments</span></span>  
 <span data-ttu-id="0099a-106">`dir` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0099a-106">`dir` (optional)</span></span>  
 <span data-ttu-id="0099a-107">Adresář, ve kterém má hledání začít.</span><span class="sxs-lookup"><span data-stu-id="0099a-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="0099a-108">Pokud není zadán, hledání začíná v adresáři projektu.</span><span class="sxs-lookup"><span data-stu-id="0099a-108">If this is not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="0099a-109">Soubory, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0099a-109">The file(s) to search for.</span></span> <span data-ttu-id="0099a-110">Zástupné znaky jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="0099a-110">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0099a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0099a-111">Remarks</span></span>  
 <span data-ttu-id="0099a-112">Možnost **-recurse** umožňuje kompilovat soubory zdrojového kódu ve všech`dir`podřízených adresářích zadaného adresáře ( ) nebo adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="0099a-112">The **-recurse** option lets you compile source code files in all child directories of either the specified directory (`dir`) or of the project directory.</span></span>  
  
 <span data-ttu-id="0099a-113">Zástupné znaky v názvu souboru můžete použít ke kompilaci všech odpovídajících souborů v adresáři projektu bez použití **-recurse**.</span><span class="sxs-lookup"><span data-stu-id="0099a-113">You can use wildcards in a file name to compile all matching files in the project directory without using **-recurse**.</span></span>  
  
 <span data-ttu-id="0099a-114">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="0099a-114">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0099a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0099a-115">Example</span></span>  
 <span data-ttu-id="0099a-116">Zkompiluje všechny soubory jazyka C# v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="0099a-116">Compiles all C# files in the current directory:</span></span>  
  
```console  
csc *.cs  
```  
  
 <span data-ttu-id="0099a-117">Zkompiluje všechny soubory jazyka C# v adresáři dir1\dir2 a všechny adresáře pod ním a generuje dir2.dll:</span><span class="sxs-lookup"><span data-stu-id="0099a-117">Compiles all of the C# files in the dir1\dir2 directory and any directories below it and generates dir2.dll:</span></span>  
  
```console  
csc -target:library -out:dir2.dll -recurse:dir1\dir2\*.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0099a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0099a-118">See also</span></span>

- [<span data-ttu-id="0099a-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0099a-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0099a-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="0099a-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
