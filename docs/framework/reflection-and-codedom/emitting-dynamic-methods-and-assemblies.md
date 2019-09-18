---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8e2b9aeb8c632efcbf8c506da4da7c6e7b408e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046089"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="3c73f-102">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="3c73f-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="3c73f-103">Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> oboru názvů, které umožňují kompilátorům nebo nástrojům generovat metadata a jazyk MSIL (Microsoft Intermediate Language) za běhu a volitelně vygenerovat soubor přenositelného spustitelného souboru (PE) na disku.</span><span class="sxs-lookup"><span data-stu-id="3c73f-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="3c73f-104">Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3c73f-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="3c73f-105">V této části je funkce poskytovaná <xref:System.Reflection.Emit> oborem názvů označována jako vygenerování reflexe.</span><span class="sxs-lookup"><span data-stu-id="3c73f-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="3c73f-106">Vygenerování reflexe poskytuje následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="3c73f-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="3c73f-107">Definujte zjednodušené globální metody za běhu, pomocí <xref:System.Reflection.Emit.DynamicMethod> třídy a spusťte je pomocí delegátů.</span><span class="sxs-lookup"><span data-stu-id="3c73f-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="3c73f-108">Definujte sestavení v době běhu a pak je spusťte nebo uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="3c73f-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="3c73f-109">Definujte sestavení za běhu, spusťte je a pak je uvolněte a umožněte uvolnění paměti, aby bylo možné znovu získat své prostředky.</span><span class="sxs-lookup"><span data-stu-id="3c73f-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="3c73f-110">Definujte moduly v nových sestaveních za běhu a pak je spusťte nebo uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="3c73f-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="3c73f-111">Definujte typy v modulech v době běhu, vytvořte instance těchto typů a volejte jejich metody.</span><span class="sxs-lookup"><span data-stu-id="3c73f-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="3c73f-112">Definujte symbolické informace pro definované moduly, které mohou být používány nástroji, jako jsou ladicí programy a profilery kódu.</span><span class="sxs-lookup"><span data-stu-id="3c73f-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="3c73f-113">Kromě spravovaných typů v <xref:System.Reflection.Emit> oboru názvů existují nespravovaná rozhraní metadat, která jsou popsána v referenční dokumentaci [rozhraní metadat](../unmanaged-api/metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="3c73f-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="3c73f-114">Spravované reflexe Emit poskytuje silnější sémantickou kontrolu chyb a vyšší úroveň abstrakce metadat než nespravované rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="3c73f-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="3c73f-115">Dalším užitečným prostředkem pro práci s metadaty a jazykem MSIL je dokumentace k Common Language Infrastructure (CLI), obzvláště "partition II: Definice metadat a sémantika "a" partition III: Sada instrukcí CIL</span><span class="sxs-lookup"><span data-stu-id="3c73f-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="3c73f-116">Dokumentace je k dispozici online na webu [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) a na webu [ECMA](https://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="3c73f-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c73f-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3c73f-117">In This Section</span></span>
  
[<span data-ttu-id="3c73f-118">Problémy se zabezpečením v generování reflexe</span><span class="sxs-lookup"><span data-stu-id="3c73f-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="3c73f-119">Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí generování reflexe.</span><span class="sxs-lookup"><span data-stu-id="3c73f-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="3c73f-120">[Postupy: Definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="3c73f-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="3c73f-121">Ukazuje, jak spustit jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="3c73f-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="3c73f-122">[Postupy: Definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="3c73f-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="3c73f-123">Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="3c73f-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="3c73f-124">[Postupy: Definování obecné metody pomocí generování reflexe](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="3c73f-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="3c73f-125">Ukazuje, jak vytvořit, vygenerovat a vyvolat jednoduchou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="3c73f-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="3c73f-126">[Kolekční sestavení pro generování dynamického typu](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="3c73f-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="3c73f-127">Zavádí kolekční sestavení, která jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="3c73f-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="3c73f-128">Reference</span><span class="sxs-lookup"><span data-stu-id="3c73f-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="3c73f-129">Zařadí do katalogu kódy instrukcí jazyka MSIL, které můžete použít k sestavení těla metody.</span><span class="sxs-lookup"><span data-stu-id="3c73f-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="3c73f-130">Obsahuje spravované třídy používané k vygenerování dynamických metod, sestavení a typů.</span><span class="sxs-lookup"><span data-stu-id="3c73f-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="3c73f-131"><xref:System.Type> Popisuje třídu, která představuje typy v spravovaných reflexích a reflexi Emit a který je klíčem k používání těchto technologií.</span><span class="sxs-lookup"><span data-stu-id="3c73f-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="3c73f-132">Obsahuje spravované třídy používané k prozkoumávání metadat a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3c73f-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c73f-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3c73f-133">Related Sections</span></span>  

[<span data-ttu-id="3c73f-134">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3c73f-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="3c73f-135">Vysvětluje, jak prozkoumat metadata a spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3c73f-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="3c73f-136">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="3c73f-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="3c73f-137">Poskytuje přehled o sestaveních v implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3c73f-137">Provides an overview of assemblies in .NET implementations.</span></span>
