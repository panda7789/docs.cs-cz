---
title: "-moduleassemblyname (možnost kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ef68b6a75d9f5bd65e7d549240dc061097f2d30c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="4a228-102">-moduleassemblyname (možnost kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4a228-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="4a228-103">Určuje sestavení, jehož neveřejným typům .netmodule přístup.</span><span class="sxs-lookup"><span data-stu-id="4a228-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a228-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a228-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a228-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a228-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="4a228-106">Název sestavení, jejichž neveřejný typy .netmodule mají přístup.</span><span class="sxs-lookup"><span data-stu-id="4a228-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a228-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a228-107">Remarks</span></span>  
 <span data-ttu-id="4a228-108">**-moduleassemblyname** by měl použít při vytváření .netmodule, a tam, kde platí následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="4a228-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
-   <span data-ttu-id="4a228-109">.netmodule potřebuje přístup k neveřejným typům v existujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="4a228-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
-   <span data-ttu-id="4a228-110">Víte, název sestavení, do které budou vytvořeny .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4a228-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
-   <span data-ttu-id="4a228-111">Existující sestavení udělil přátelských sestavení přístup do sestavení, do které budou vytvořeny .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4a228-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="4a228-112">Další informace o vytváření .netmodule najdete v tématu [-target: module (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="4a228-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="4a228-113">Další informace o přátelských sestavení najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4a228-113">For more information on friend assemblies, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="4a228-114">Tato možnost není k dispozici v rámci vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4a228-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="4a228-115">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="4a228-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a228-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a228-116">Example</span></span>  
 <span data-ttu-id="4a228-117">Tato ukázka vytvoří sestavení s typem privátní a sestavení s názvem csman_an_assembly udávající přátelských sestavení přístup.</span><span class="sxs-lookup"><span data-stu-id="4a228-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="4a228-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a228-118">Example</span></span>  
 <span data-ttu-id="4a228-119">Tato ukázka vytvoří .netmodule, který přistupuje k typu neveřejný v sestavení moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="4a228-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="4a228-120">Musíte znát, že tento .netmodule bude vytvořen v sestavení nazvaném csman_an_assembly, můžeme určit **- moduleassemblyname**, což .netmodule pro přístup k neveřejný typy v sestavení, které má povolen přátelských sestavení přístup k csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="4a228-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="4a228-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a228-121">Example</span></span>  
 <span data-ttu-id="4a228-122">Tento příklad vytvoří sestavení csman_an_assembly, odkazy na dříve vytvořené sestavení a .netmodule.</span><span class="sxs-lookup"><span data-stu-id="4a228-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
 <span data-ttu-id="4a228-123">**An_Internal_Class.test názvem**</span><span class="sxs-lookup"><span data-stu-id="4a228-123">**An_Internal_Class.Test called**</span></span>  
## <a name="see-also"></a><span data-ttu-id="4a228-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a228-124">See Also</span></span>  
 [<span data-ttu-id="4a228-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4a228-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4a228-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4a228-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
