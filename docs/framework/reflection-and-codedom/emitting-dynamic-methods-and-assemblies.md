---
title: Generování dynamických metod a sestavení
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180531"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="0cfd5-102">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="0cfd5-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="0cfd5-103">Tato část popisuje sadu spravovaných typů v oboru <xref:System.Reflection.Emit> názvů, které umožňují kompilátoru nebo nástroji vyzařovat metadata a zprostředkující jazyk Microsoft (MSIL) za běhu a volitelně generovat přenosný spustitelný soubor (PE) na disku.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="0cfd5-104">Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="0cfd5-105">V této části funkce poskytované obor <xref:System.Reflection.Emit> názvů se označuje jako odraz emit.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="0cfd5-106">Reflexe vyzařují poskytuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="0cfd5-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="0cfd5-107">Definujte zjednodušené globální metody <xref:System.Reflection.Emit.DynamicMethod> za běhu pomocí třídy a spusťte je pomocí delegátů.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="0cfd5-108">Definujte sestavení za běhu a pak je spusťte a/nebo je uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="0cfd5-109">Definujte sestavení za běhu, spusťte je a pak je uvolněte a povolte uvolnění paměti pro uvolnění jejich prostředků.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="0cfd5-110">Definujte moduly v nových sestaveních za běhu a potom je spusťte a/nebo je uložte na disk.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="0cfd5-111">Definujte typy v modulech za běhu, vytvořte instance těchto typů a vyvolat jejich metody.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="0cfd5-112">Definujte symbolické informace pro definované moduly, které mohou být použity nástroji, jako jsou ladicí programy a profilovací programy kódu.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="0cfd5-113">Kromě spravovaných typů <xref:System.Reflection.Emit> v oboru názvů existují nespravovaná metadata rozhraní, které jsou popsány v dokumentaci metadat [rozhraní](../unmanaged-api/metadata/metadata-interfaces.md) referenční.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="0cfd5-114">Spravovaný odraz emit poskytuje silnější sémantické kontroly chyb a vyšší úroveň abstrakce metadat než nespravované metadata rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="0cfd5-115">Dalším užitečným zdrojem informací pro práci s metadaty a jazykem MSIL je dokumentace common language infrastructure (CLI), zejména "Partition II: Metadata Definition and Sémantics" a "Partition III: CIL Instruction Set".</span><span class="sxs-lookup"><span data-stu-id="0cfd5-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="0cfd5-116">Dokumentace je k dispozici online na [webových stránkách společnosti Ecma](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="0cfd5-116">The documentation is available online at the [Ecma Web site](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0cfd5-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0cfd5-117">In This Section</span></span>
  
[<span data-ttu-id="0cfd5-118">Bezpečnostní otázky v reflexi vyzařují</span><span class="sxs-lookup"><span data-stu-id="0cfd5-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="0cfd5-119">Popisuje problémy se zabezpečením související s vytvářením dynamických sestavení pomocí odrazu vyzařovat.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="0cfd5-120">[Postup: Definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) Ukazuje, jak provést jednoduchou dynamickou metodu a dynamickou metodu vázanou na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="0cfd5-121">[Postup: Definování obecného typu s odrazem emitují](how-to-define-a-generic-type-with-reflection-emit.md) Ukazuje, jak vytvořit jednoduchý obecný typ se dvěma parametry typu, jak použít třídu, rozhraní a speciální omezení parametrů typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-121">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="0cfd5-122">[Postup: Definování obecné metody s odrazem vyzařovat](how-to-define-a-generic-method-with-reflection-emit.md) Ukazuje, jak vytvořit, vyzařovat a vyvolat jednoduchou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-122">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="0cfd5-123">[Sběratelské sestavy pro dynamické generování typů](collectible-assemblies.md) Zavádí sběratelská sestavení, což jsou dynamická sestavení, která lze uvolnit bez uvolnění domény aplikace, ve které byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-123">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="0cfd5-124">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="0cfd5-124">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="0cfd5-125">Katalogy kódy instrukcí MSIL, které můžete použít k sestavení těla metod.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-125">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="0cfd5-126">Obsahuje spravované třídy používané k emitování dynamických metod, sestavení a typů.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-126">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="0cfd5-127">Popisuje třídu, <xref:System.Type> která představuje typy ve spravované reflexe a odrazu vyzařovat a který je klíčem k použití těchto technologií.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-127">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="0cfd5-128">Obsahuje spravované třídy používané k prozkoumání metadat a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-128">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0cfd5-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0cfd5-129">Related Sections</span></span>  

[<span data-ttu-id="0cfd5-130">Reflexe</span><span class="sxs-lookup"><span data-stu-id="0cfd5-130">Reflection</span></span>](reflection.md)  
<span data-ttu-id="0cfd5-131">Vysvětluje, jak prozkoumat metadata a spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-131">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="0cfd5-132">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="0cfd5-132">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="0cfd5-133">Poskytuje přehled sestavení v implementacích rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="0cfd5-133">Provides an overview of assemblies in .NET implementations.</span></span>
