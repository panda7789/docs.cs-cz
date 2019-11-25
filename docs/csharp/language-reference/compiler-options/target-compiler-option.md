---
title: -target (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204517"
---
# <a name="-target-c-compiler-options"></a><span data-ttu-id="e1123-102">-target (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="e1123-102">-target (C# Compiler Options)</span></span>
<span data-ttu-id="e1123-103">The **-target** compiler option can be specified in one of four forms:</span><span class="sxs-lookup"><span data-stu-id="e1123-103">The **-target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="e1123-104">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="e1123-104">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="e1123-105">To create an .exe file for Windows 8.x Store apps.</span><span class="sxs-lookup"><span data-stu-id="e1123-105">To create an .exe file for Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="e1123-106">-target:exe</span><span class="sxs-lookup"><span data-stu-id="e1123-106">-target:exe</span></span>](./target-exe-compiler-option.md)  
 <span data-ttu-id="e1123-107">To create an .exe file.</span><span class="sxs-lookup"><span data-stu-id="e1123-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="e1123-108">-target:library</span><span class="sxs-lookup"><span data-stu-id="e1123-108">-target:library</span></span>](./target-library-compiler-option.md)  
 <span data-ttu-id="e1123-109">To create a code library.</span><span class="sxs-lookup"><span data-stu-id="e1123-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="e1123-110">-target:module</span><span class="sxs-lookup"><span data-stu-id="e1123-110">-target:module</span></span>](./target-module-compiler-option.md)  
 <span data-ttu-id="e1123-111">To create a module.</span><span class="sxs-lookup"><span data-stu-id="e1123-111">To create a module.</span></span>  
  
 [<span data-ttu-id="e1123-112">-target:winexe</span><span class="sxs-lookup"><span data-stu-id="e1123-112">-target:winexe</span></span>](./target-winexe-compiler-option.md)  
 <span data-ttu-id="e1123-113">To create a Windows program.</span><span class="sxs-lookup"><span data-stu-id="e1123-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="e1123-114">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="e1123-114">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)  
 <span data-ttu-id="e1123-115">To create an intermediate .winmdobj file.</span><span class="sxs-lookup"><span data-stu-id="e1123-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="e1123-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span><span class="sxs-lookup"><span data-stu-id="e1123-116">Unless you specify **-target:module**, **-target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="e1123-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="e1123-117">For more information, see [Assemblies in .NET](../../../standard/assembly/index.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="e1123-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span><span class="sxs-lookup"><span data-stu-id="e1123-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="e1123-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="e1123-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="e1123-120">The compiler creates only one assembly manifest per compilation.</span><span class="sxs-lookup"><span data-stu-id="e1123-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="e1123-121">Information about all files in a compilation is placed in the assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="e1123-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="e1123-122">All output files except those created with **-target:module** can contain an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="e1123-122">All output files except those created with **-target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="e1123-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span><span class="sxs-lookup"><span data-stu-id="e1123-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="e1123-124">No matter what the first output file is ( **-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules ( **-target:module**).</span><span class="sxs-lookup"><span data-stu-id="e1123-124">No matter what the first output file is (**-target:exe**, **-target:winexe**, **-target:library** or **-target:module**), any other output files produced in the same compilation must be modules (**-target:module**).</span></span>  
  
 <span data-ttu-id="e1123-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span><span class="sxs-lookup"><span data-stu-id="e1123-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="e1123-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e1123-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1123-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1123-127">See also</span></span>

- [<span data-ttu-id="e1123-128">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e1123-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e1123-129">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e1123-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="e1123-130">-subsystemversion (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="e1123-130">-subsystemversion (C# Compiler Options)</span></span>](./subsystemversion-compiler-option.md)
