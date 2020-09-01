---
description: -addmodule – (možnosti kompilátoru C#)
title: -addmodule – (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: bcc615d52aec0a09ebf3913b3ece71f2cbfcbda9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126122"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="f5869-103">-addmodule – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f5869-103">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="f5869-104">Tato možnost přidá modul, který byl vytvořen s možností cíl: modul přepnutí na aktuální kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f5869-104">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5869-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5869-105">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5869-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f5869-106">Arguments</span></span>  
 <span data-ttu-id="f5869-107">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="f5869-107">`file`, `file2`</span></span>  
 <span data-ttu-id="f5869-108">Výstupní soubor, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="f5869-108">An output file that contains metadata.</span></span> <span data-ttu-id="f5869-109">Soubor nemůže obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5869-109">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="f5869-110">Chcete-li importovat více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.</span><span class="sxs-lookup"><span data-stu-id="f5869-110">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5869-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5869-111">Remarks</span></span>  
 <span data-ttu-id="f5869-112">Všechny moduly přidané pomocí **-addmodule –** musí být ve stejném adresáři jako výstupní soubor v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f5869-112">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="f5869-113">To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f5869-113">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="f5869-114">Pokud modul není v adresáři aplikace v době běhu, zobrazí se <xref:System.TypeLoadException> .</span><span class="sxs-lookup"><span data-stu-id="f5869-114">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="f5869-115">`file` nemůže obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5869-115">`file` cannot contain an assembly.</span></span> <span data-ttu-id="f5869-116">Například pokud byl výstupní soubor vytvořen pomocí [-target: Module](./target-module-compiler-option.md), jeho metadata lze importovat pomocí **-addmodule –**.</span><span class="sxs-lookup"><span data-stu-id="f5869-116">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="f5869-117">Pokud byl výstupní soubor vytvořen s možností **-target** jinou než **-target: Module**, jeho metadata nelze importovat pomocí **-addmodule –** , ale lze je importovat s [odkazem](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="f5869-117">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="f5869-118">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici; projekt nemůže odkazovat na modul.</span><span class="sxs-lookup"><span data-stu-id="f5869-118">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="f5869-119">Tuto možnost kompilátoru nelze navíc změnit programově.</span><span class="sxs-lookup"><span data-stu-id="f5869-119">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5869-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5869-120">Example</span></span>  
 <span data-ttu-id="f5869-121">Zkompilujte zdrojový soubor `input.cs` a přidejte metadata z `metad1.netmodule` a `metad2.netmodule` do sestavení `out.exe` :</span><span class="sxs-lookup"><span data-stu-id="f5869-121">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5869-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5869-122">See also</span></span>

- [<span data-ttu-id="f5869-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="f5869-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f5869-124">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f5869-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="f5869-125">Vícesouborové sestavení</span><span class="sxs-lookup"><span data-stu-id="f5869-125">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="f5869-126">Postupy: sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="f5869-126">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
