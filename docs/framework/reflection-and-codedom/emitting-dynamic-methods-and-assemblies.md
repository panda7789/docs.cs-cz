---
title: Generování dynamických metod a sestavení
description: Generuje dynamické metody a sestavení pomocí oboru názvů System. Reflection. Emit, který umožňuje kompilátoru nebo nástroji generovat metadata a kód jazyka MSIL za běhu.
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 76d2a83943d9df06cc66cf86c6869f18fac2a12c
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475044"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="2a86f-103">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="2a86f-103">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="2a86f-104">Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> oboru názvů, které umožňují kompilátorům nebo nástrojům generovat metadata a jazyk MSIL (Microsoft Intermediate Language) za běhu a volitelně vygenerovat soubor přenositelného spustitelného souboru (PE) na disku.</span><span class="sxs-lookup"><span data-stu-id="2a86f-104">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="2a86f-105">Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2a86f-105">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="2a86f-106">V této části je funkce poskytovaná <xref:System.Reflection.Emit> oborem názvů označována jako vygenerování reflexe.</span><span class="sxs-lookup"><span data-stu-id="2a86f-106">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="2a86f-107">Vygenerování reflexe poskytuje následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="2a86f-107">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="2a86f-108">Definujte zjednodušené globální metody za běhu, pomocí <xref:System.Reflection.Emit.DynamicMethod> třídy a spusťte je pomocí delegátů.</span><span class="sxs-lookup"><span data-stu-id="2a86f-108">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="2a86f-109">Definujte sestavení v době běhu a pak je spusťte nebo uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="2a86f-109">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="2a86f-110">Definujte sestavení za běhu, spusťte je a pak je uvolněte a umožněte uvolnění paměti, aby bylo možné znovu získat své prostředky.</span><span class="sxs-lookup"><span data-stu-id="2a86f-110">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="2a86f-111">Definujte moduly v nových sestaveních za běhu a pak je spusťte nebo uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="2a86f-111">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="2a86f-112">Definujte typy v modulech v době běhu, vytvořte instance těchto typů a volejte jejich metody.</span><span class="sxs-lookup"><span data-stu-id="2a86f-112">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="2a86f-113">Definujte symbolické informace pro definované moduly, které mohou být používány nástroji, jako jsou ladicí programy a profilery kódu.</span><span class="sxs-lookup"><span data-stu-id="2a86f-113">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="2a86f-114">Kromě spravovaných typů v <xref:System.Reflection.Emit> oboru názvů existují nespravovaná rozhraní metadat, která jsou popsána v referenční dokumentaci [rozhraní metadat](../unmanaged-api/metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="2a86f-114">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="2a86f-115">Spravované reflexe Emit poskytuje silnější sémantickou kontrolu chyb a vyšší úroveň abstrakce metadat než nespravované rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="2a86f-115">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="2a86f-116">Dalším užitečným prostředkem pro práci s metadaty a jazykem MSIL je dokumentace Common Language Infrastructure (CLI), zejména oddíl II: definice metadat a sémantika a oddíl III: sada instrukcí CIL.</span><span class="sxs-lookup"><span data-stu-id="2a86f-116">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="2a86f-117">Dokumentace je k dispozici online na webu [ECMA](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="2a86f-117">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a86f-118">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2a86f-118">In This Section</span></span>
  
[<span data-ttu-id="2a86f-119">Problémy se zabezpečením v generování reflexe</span><span class="sxs-lookup"><span data-stu-id="2a86f-119">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="2a86f-120">Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí generování reflexe.</span><span class="sxs-lookup"><span data-stu-id="2a86f-120">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="2a86f-121">[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) Ukazuje, jak spustit jednoduchou dynamickou metodu a dynamickou metodu svázanou s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="2a86f-121">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="2a86f-122">[Postupy: definování obecného typu pomocí generování reflexe](how-to-define-a-generic-type-with-reflection-emit.md) Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="2a86f-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="2a86f-123">[Postupy: definování obecné metody pomocí generování reflexe](how-to-define-a-generic-method-with-reflection-emit.md) Ukazuje, jak vytvořit, vygenerovat a vyvolat jednoduchou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="2a86f-123">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="2a86f-124">[Kolekční sestavení pro generování dynamického typu](collectible-assemblies.md) Zavádí kolekční sestavení, která jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="2a86f-124">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="2a86f-125">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2a86f-125">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="2a86f-126">Zařadí do katalogu kódy instrukcí jazyka MSIL, které můžete použít k sestavení těla metody.</span><span class="sxs-lookup"><span data-stu-id="2a86f-126">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="2a86f-127">Obsahuje spravované třídy používané k vygenerování dynamických metod, sestavení a typů.</span><span class="sxs-lookup"><span data-stu-id="2a86f-127">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="2a86f-128">Popisuje <xref:System.Type> třídu, která představuje typy v spravovaných reflexích a reflexi Emit a který je klíčem k používání těchto technologií.</span><span class="sxs-lookup"><span data-stu-id="2a86f-128">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="2a86f-129">Obsahuje spravované třídy používané k prozkoumávání metadat a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2a86f-129">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a86f-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2a86f-130">Related Sections</span></span>  

[<span data-ttu-id="2a86f-131">Reflexe</span><span class="sxs-lookup"><span data-stu-id="2a86f-131">Reflection</span></span>](reflection.md)  
<span data-ttu-id="2a86f-132">Vysvětluje, jak prozkoumat metadata a spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="2a86f-132">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="2a86f-133">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="2a86f-133">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="2a86f-134">Poskytuje přehled o sestaveních v implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2a86f-134">Provides an overview of assemblies in .NET implementations.</span></span>
