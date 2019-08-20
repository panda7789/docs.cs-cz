---
title: -moduleassemblyname – (C# možnost kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: d57279128c0909ba3e62d55d596705cfde6be75c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606661"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="b1b15-102">-moduleassemblyname – (C# možnost kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b1b15-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="b1b15-103">Určuje sestavení, jehož neveřejné typy a. netmodule mají přístup.</span><span class="sxs-lookup"><span data-stu-id="b1b15-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b15-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1b15-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b1b15-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b1b15-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="b1b15-106">Název sestavení, jehož neveřejné typy má. netmodule, ke kterému má přístup.</span><span class="sxs-lookup"><span data-stu-id="b1b15-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1b15-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1b15-107">Remarks</span></span>  
 <span data-ttu-id="b1b15-108">**-moduleassemblyname –** by měla být použita při sestavování. netmodule a kde jsou splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="b1b15-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="b1b15-109">Modul. netmodule potřebuje přístup k neveřejným typům v existujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1b15-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="b1b15-110">Znáte název sestavení, do kterého bude sestaven. netmodule.</span><span class="sxs-lookup"><span data-stu-id="b1b15-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="b1b15-111">Existující sestavení má udělený přístup pro sestavení typu Friend k sestavení, do kterého bude sestaven. netmodule.</span><span class="sxs-lookup"><span data-stu-id="b1b15-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="b1b15-112">Další informace o vytváření. netmodule naleznete v tématu [-target: Module (C# možnosti kompilátoru)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b1b15-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="b1b15-113">Další informace o Friend sestaveních naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b1b15-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="b1b15-114">Tato možnost není k dispozici v rámci vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b1b15-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="b1b15-115">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="b1b15-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b15-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1b15-116">Example</span></span>  
 <span data-ttu-id="b1b15-117">Tato ukázka sestaví sestavení s privátním typem a poskytuje přítel přístup k sestavení s názvem csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="b1b15-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b1b15-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1b15-118">Example</span></span>  
 <span data-ttu-id="b1b15-119">Tato ukázka sestaví. netmodule, který přistupuje k neveřejnému typu v sestavení moduleassemblyname_1. dll.</span><span class="sxs-lookup"><span data-stu-id="b1b15-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="b1b15-120">Díky tomu, že tento modul netmodule bude sestaven do sestavení s názvem csman_an_assembly, můžeme specifikovat **-moduleassemblyname –** , což umožňuje rozhraní. netmodule přístup k neveřejným typům v sestavení, které udělily přístup přítel k sestavení csman_an_. shromážděním.</span><span class="sxs-lookup"><span data-stu-id="b1b15-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="b1b15-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1b15-121">Example</span></span>  
 <span data-ttu-id="b1b15-122">Tento vzorový kód sestaví sestavení csman_an_assembly a odkazuje na dřív sestavené sestavení a. netmodule.</span><span class="sxs-lookup"><span data-stu-id="b1b15-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="b1b15-123">**An_Internal_Class. test volal**</span><span class="sxs-lookup"><span data-stu-id="b1b15-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="b1b15-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1b15-124">See also</span></span>

- [<span data-ttu-id="b1b15-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1b15-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b1b15-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b1b15-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
