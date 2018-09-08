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
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183129"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="a2e67-102">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="a2e67-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="a2e67-103">Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> obor názvů, které umožní, aby kompilátor nebo nástroj generoval metadata a jazyk Microsoft intermediate language (MSIL) v době běhu a volitelně vygenerovat soubor (PE portable executable) na disku.</span><span class="sxs-lookup"><span data-stu-id="a2e67-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="a2e67-104">Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a2e67-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="a2e67-105">V této části poskytuje funkce <xref:System.Reflection.Emit> obor názvů se označuje jako reflexe vygenerovat.</span><span class="sxs-lookup"><span data-stu-id="a2e67-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="a2e67-106">Emitování reflexe poskytuje následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="a2e67-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="a2e67-107">Definovat jednoduchý globální metody za běhu použití <xref:System.Reflection.Emit.DynamicMethod> třídy a spouštějte je pomocí delegátů.</span><span class="sxs-lookup"><span data-stu-id="a2e67-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="a2e67-108">Definice sestavení v době běhu a jejich spuštění nebo uložení na disk.</span><span class="sxs-lookup"><span data-stu-id="a2e67-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="a2e67-109">Definice sestavení v době běhu, spustit, je uvolnit a povolit uvolňování uvolnit jejich prostředky.</span><span class="sxs-lookup"><span data-stu-id="a2e67-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="a2e67-110">Definování modulů v nová sestavení v době běhu a spouštět nebo uložit na disk.</span><span class="sxs-lookup"><span data-stu-id="a2e67-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="a2e67-111">Definování typů v modulech v době běhu, vytváření instancí těchto typů a vyvolání jejich metod.</span><span class="sxs-lookup"><span data-stu-id="a2e67-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="a2e67-112">Definujte informace o symbolech pro definovaný moduly, které můžete používat nástroje, jako je například ladicí programy a profilery kódu.</span><span class="sxs-lookup"><span data-stu-id="a2e67-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="a2e67-113">Kromě spravovaných typů v <xref:System.Reflection.Emit> obor názvů, nejsou nespravované metadat rozhraní, které jsou popsány v [rozhraní metadat](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) referenční dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="a2e67-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="a2e67-114">Emitování reflexe spravované nabízí silnější kontrolu sémantických chyb a vyšší úroveň abstrakce metadata než rozhraní nespravované metadat.</span><span class="sxs-lookup"><span data-stu-id="a2e67-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="a2e67-115">Další užitečné zdroje pro práci s metadata a jazyk MSIL je dokumentace společné jazykové infrastruktury (CLI), zejména "Oddíl II: Metadata definice a sémantika" a "Oddílu III: soubor CIL se NAČTE sadu instrukcí".</span><span class="sxs-lookup"><span data-stu-id="a2e67-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="a2e67-116">Dokumentace je k dispozici online na [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) a [webu Ecma](https://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="a2e67-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2e67-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2e67-117">In This Section</span></span>
  
[<span data-ttu-id="a2e67-118">Bezpečnostní problémy v generování reflexe</span><span class="sxs-lookup"><span data-stu-id="a2e67-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="a2e67-119">Popisuje problémy související s vytvářením dynamických sestavení pomocí operace reflection emit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a2e67-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="a2e67-120">[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="a2e67-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="a2e67-121">Ukazuje, jak provést jednoduchou dynamickou metodu a dynamická metoda svázána s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="a2e67-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="a2e67-122">[Postupy: definování obecného typu pomocí reflexe generování](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="a2e67-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="a2e67-123">Ukazuje, jak vytvořit jednoduchý obecný typ s dvěma parametry typu, jak použít třídy, rozhraní a zvláštní omezení pro parametry typu a jak vytvořit členy, které používají parametry typu třídy jako typy parametrů a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="a2e67-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="a2e67-124">[Postupy: definování obecné metody pomocí reflexe generování](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="a2e67-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="a2e67-125">Ukazuje, jak vytvořit, generovat a vyvolání jednoduchou obecnou metodu.</span><span class="sxs-lookup"><span data-stu-id="a2e67-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="a2e67-126">[Kolekční sestavení pro generování dynamických typů](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="a2e67-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="a2e67-127">Zavádí kolekční sestavení, které jsou dynamické sestavení, které může být uvolněno bez uvolnění domény aplikace, ve kterém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="a2e67-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="a2e67-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a2e67-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="a2e67-129">Katalogy kódy instrukce jazyka MSIL, které můžete použít k sestavení těl metod.</span><span class="sxs-lookup"><span data-stu-id="a2e67-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="a2e67-130">Obsahuje spravované třídy použít ke generování dynamických metod a sestavení, typy.</span><span class="sxs-lookup"><span data-stu-id="a2e67-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="a2e67-131">Popisuje <xref:System.Type> reflexe spravované třídy, která představuje typy v generování reflexe a který je klíčem k používání těchto technologií.</span><span class="sxs-lookup"><span data-stu-id="a2e67-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="a2e67-132">Obsahuje spravované třídy používané k prozkoumání metadata a spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a2e67-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2e67-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a2e67-133">Related Sections</span></span>  
 [<span data-ttu-id="a2e67-134">Reflexe</span><span class="sxs-lookup"><span data-stu-id="a2e67-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="a2e67-135">Vysvětluje, jak prozkoumat metadata a spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="a2e67-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="a2e67-136">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="a2e67-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="a2e67-137">Poskytuje přehled sestavení v implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="a2e67-137">Provides an overview of assemblies in .NET implementations.</span></span>
