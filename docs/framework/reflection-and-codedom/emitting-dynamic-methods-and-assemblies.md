---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 578851bed188921324e3c25e533b3466068dee3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446781"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="97614-102">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="97614-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="97614-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span><span class="sxs-lookup"><span data-stu-id="97614-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="97614-104">Script engines and compilers are the primary users of this namespace.</span><span class="sxs-lookup"><span data-stu-id="97614-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="97614-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span><span class="sxs-lookup"><span data-stu-id="97614-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="97614-106">Reflection emit provides the following capabilities:</span><span class="sxs-lookup"><span data-stu-id="97614-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="97614-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span><span class="sxs-lookup"><span data-stu-id="97614-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="97614-108">Define assemblies at run time and then run them and/or save them to disk.</span><span class="sxs-lookup"><span data-stu-id="97614-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="97614-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span><span class="sxs-lookup"><span data-stu-id="97614-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="97614-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span><span class="sxs-lookup"><span data-stu-id="97614-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="97614-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span><span class="sxs-lookup"><span data-stu-id="97614-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="97614-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span><span class="sxs-lookup"><span data-stu-id="97614-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="97614-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span><span class="sxs-lookup"><span data-stu-id="97614-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="97614-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span><span class="sxs-lookup"><span data-stu-id="97614-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="97614-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span><span class="sxs-lookup"><span data-stu-id="97614-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="97614-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="97614-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97614-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="97614-117">In This Section</span></span>
  
[<span data-ttu-id="97614-118">Security issues in reflection emit</span><span class="sxs-lookup"><span data-stu-id="97614-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="97614-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span><span class="sxs-lookup"><span data-stu-id="97614-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="97614-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="97614-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="97614-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span><span class="sxs-lookup"><span data-stu-id="97614-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="97614-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="97614-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="97614-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span><span class="sxs-lookup"><span data-stu-id="97614-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="97614-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="97614-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="97614-125">Shows how to create, emit, and invoke a simple generic method.</span><span class="sxs-lookup"><span data-stu-id="97614-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="97614-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="97614-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="97614-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span><span class="sxs-lookup"><span data-stu-id="97614-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="97614-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="97614-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="97614-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span><span class="sxs-lookup"><span data-stu-id="97614-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="97614-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span><span class="sxs-lookup"><span data-stu-id="97614-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="97614-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span><span class="sxs-lookup"><span data-stu-id="97614-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="97614-132">Contains managed classes used to explore metadata and managed code.</span><span class="sxs-lookup"><span data-stu-id="97614-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="97614-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="97614-133">Related Sections</span></span>  

[<span data-ttu-id="97614-134">Reflexe</span><span class="sxs-lookup"><span data-stu-id="97614-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="97614-135">Explains how to explore metadata and managed code.</span><span class="sxs-lookup"><span data-stu-id="97614-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="97614-136">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="97614-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="97614-137">Provides an overview of assemblies in .NET implementations.</span><span class="sxs-lookup"><span data-stu-id="97614-137">Provides an overview of assemblies in .NET implementations.</span></span>
