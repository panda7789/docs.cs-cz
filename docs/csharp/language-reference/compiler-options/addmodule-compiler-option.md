---
title: -addmodule – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
ms.openlocfilehash: f2fae0be3ba958dc9776ed253c178933e4f76024
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69607043"
---
# <a name="-addmodule-c-compiler-options"></a><span data-ttu-id="a0116-102">-addmodule – (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="a0116-102">-addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="a0116-103">Tato možnost přidá modul, který byl vytvořen s možností cíl: modul přepnutí na aktuální kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a0116-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0116-104">Syntax</span></span>  
  
```console  
-addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0116-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a0116-105">Arguments</span></span>  
 <span data-ttu-id="a0116-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="a0116-106">`file`, `file2`</span></span>  
 <span data-ttu-id="a0116-107">Výstupní soubor, který obsahuje metadata.</span><span class="sxs-lookup"><span data-stu-id="a0116-107">An output file that contains metadata.</span></span> <span data-ttu-id="a0116-108">Soubor nemůže obsahovat manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0116-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="a0116-109">Chcete-li importovat více než jeden soubor, oddělte názvy souborů čárkou nebo středníkem.</span><span class="sxs-lookup"><span data-stu-id="a0116-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0116-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0116-110">Remarks</span></span>  
 <span data-ttu-id="a0116-111">Všechny moduly přidané pomocí **-addmodule –** musí být ve stejném adresáři jako výstupní soubor v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a0116-111">All modules added with **-addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="a0116-112">To znamená, že můžete určit modul v jakémkoli adresáři v době kompilace, ale modul musí být v adresáři aplikace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a0116-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="a0116-113">Pokud modul není v adresáři aplikace v době běhu, <xref:System.TypeLoadException>zobrazí se.</span><span class="sxs-lookup"><span data-stu-id="a0116-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="a0116-114">`file`nemůže obsahovat sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0116-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="a0116-115">Například pokud byl výstupní soubor vytvořen pomocí [-target: Module](./target-module-compiler-option.md), jeho metadata lze importovat pomocí **-addmodule –** .</span><span class="sxs-lookup"><span data-stu-id="a0116-115">For example, if the output file was created with [-target:module](./target-module-compiler-option.md), its metadata can be imported with **-addmodule**.</span></span>  
  
 <span data-ttu-id="a0116-116">Pokud byl výstupní soubor vytvořen s možností **-target** jinou než **-target: Module**, jeho metadata nelze importovat pomocí **-addmodule –** , ale lze je importovat s odkazem [](./reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a0116-116">If the output file was created with a **-target** option other than **-target:module**, its metadata cannot be imported with **-addmodule** but can be imported with [-reference](./reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a0116-117">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici; projekt nemůže odkazovat na modul.</span><span class="sxs-lookup"><span data-stu-id="a0116-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="a0116-118">Tuto možnost kompilátoru nelze navíc změnit programově.</span><span class="sxs-lookup"><span data-stu-id="a0116-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0116-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0116-119">Example</span></span>  
 <span data-ttu-id="a0116-120">Zkompilujte zdrojový soubor `input.cs` a přidejte metadata z `metad1.netmodule` a `metad2.netmodule` do sestavení `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="a0116-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc -addmodule:metad1.netmodule;metad2.netmodule -out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0116-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0116-121">See also</span></span>

- [<span data-ttu-id="a0116-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0116-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a0116-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a0116-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a0116-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="a0116-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="a0116-125">Postupy: Sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="a0116-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)
