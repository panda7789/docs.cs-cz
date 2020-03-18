---
title: -addmodule (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: 148a63c37cfbc4c60448adccde10947e91e22bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970176"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="4e3b2-102">-addmodule (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4e3b2-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="4e3b2-103">Tato možnost přidá modul, který byl vytvořen s přepínačem target:module do aktuální kompilace.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e3b2-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e3b2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4e3b2-105">Arguments</span></span>  
 <span data-ttu-id="4e3b2-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="4e3b2-106">`file`, `file2`</span></span>  
 <span data-ttu-id="4e3b2-107">Výstupní soubor, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-107">An output file that contains metadata.</span></span> <span data-ttu-id="4e3b2-108">Soubor nemůže obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="4e3b2-109">Chcete-li importovat více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e3b2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e3b2-110">Remarks</span></span>  
 <span data-ttu-id="4e3b2-111">Všechny moduly přidané s **-addmodule** musí být ve stejném adresáři jako výstupní soubor za běhu.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="4e3b2-112">To znamená, že můžete zadat modul v libovolném adresáři v době kompilace, ale modul musí být v adresáři aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="4e3b2-113">Pokud modul není v adresáři aplikace za běhu, <xref:System.TypeLoadException>získáte .</span><span class="sxs-lookup"><span data-stu-id="4e3b2-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="4e3b2-114">`file`nemůže obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="4e3b2-115">Například pokud výstupní soubor byl vytvořen s [-target:module](./target-module-compiler-option.md), jeho metadata lze importovat s **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="4e3b2-116">Pokud byl výstupní soubor vytvořen s jinou volbou **-target** než **-target:module**, jeho metadata nelze importovat pomocí **modulu -addmodule,** ale lze jej importovat pomocí [-reference](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4e3b2-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4e3b2-117">Tato možnost kompilátoru není k dispozici v sadě Visual Studio; projekt nemůže odkazovat na modul.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="4e3b2-118">Kromě toho tuto možnost kompilátoru nelze změnit programově.</span><span class="sxs-lookup"><span data-stu-id="4e3b2-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e3b2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e3b2-119">Example</span></span>  
 <span data-ttu-id="4e3b2-120">Kompilujte `input.cs` zdrojový soubor `metad1.netmodule` a `metad2.netmodule` přidejte metadata z a k vytvoření `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="4e3b2-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e3b2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e3b2-121">See also</span></span>

- [<span data-ttu-id="4e3b2-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e3b2-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4e3b2-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4e3b2-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="4e3b2-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="4e3b2-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="4e3b2-125">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="4e3b2-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
