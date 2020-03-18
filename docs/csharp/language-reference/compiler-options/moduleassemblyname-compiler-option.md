---
title: -moduleassemblyname (C# Compiler Option)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173715"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="7f9e3-102">-moduleassemblyname (C# Compiler Option)</span><span class="sxs-lookup"><span data-stu-id="7f9e3-102">-moduleassemblyname (C# Compiler Option)</span></span>
<span data-ttu-id="7f9e3-103">Určuje sestavení, jehož neveřejné typy .netmodule přístup.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-103">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f9e3-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f9e3-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7f9e3-105">Arguments</span></span>  
 `assembly_name`  
 <span data-ttu-id="7f9e3-106">Název sestavení, jehož neveřejné typy .netmodule přístup.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-106">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f9e3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f9e3-107">Remarks</span></span>  
 <span data-ttu-id="7f9e3-108">**-moduleassemblyname** by měl být použit při vytváření .netmodule a kde jsou splněny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="7f9e3-108">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="7f9e3-109">Modul .netmodul potřebuje přístup k neveřejným typům v existujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-109">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="7f9e3-110">Znáte název sestavení, do kterého bude vytvořen modul .netmodule.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-110">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="7f9e3-111">Existující sestavení udělilo friend assembly přístup k sestavení, do kterého bude vytvořen modul .netmodule.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-111">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="7f9e3-112">Další informace o vytváření .netmodule naleznete v tématu [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7f9e3-112">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="7f9e3-113">Další informace o sestaveních přátel naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="7f9e3-113">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="7f9e3-114">Tato možnost není k dispozici z vývojového prostředí. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-114">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="7f9e3-115">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-115">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f9e3-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f9e3-116">Example</span></span>  
 <span data-ttu-id="7f9e3-117">Tato ukázka vytvoří sestavení s privátním typem a která poskytuje přátelské sestavení přístup k sestavení s názvem csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-117">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7f9e3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f9e3-118">Example</span></span>  
 <span data-ttu-id="7f9e3-119">Tato ukázka vytvoří .netmodule, který přistupuje k neveřejnému typu v sestavení moduleassemblyname_1.dll.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-119">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="7f9e3-120">Vědomím, že tento .netmodule bude integrován do sestavení s názvem csman_an_assembly, můžeme zadat **-moduleassemblyname**, což umožňuje .netmodule pro přístup k neveřejným typům v sestavení, které udělilo přístup k sestavení friend csman_an_assembly.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-120">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7f9e3-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f9e3-121">Example</span></span>  
 <span data-ttu-id="7f9e3-122">Tento ukázkový kód vytvoří sestavení csman_an_assembly, odkazující na dříve sestavené sestavení a .netmodule.</span><span class="sxs-lookup"><span data-stu-id="7f9e3-122">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
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
  
<span data-ttu-id="7f9e3-123">**An_Internal_Class.Test volal**</span><span class="sxs-lookup"><span data-stu-id="7f9e3-123">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="7f9e3-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f9e3-124">See also</span></span>

- [<span data-ttu-id="7f9e3-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f9e3-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7f9e3-126">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="7f9e3-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
