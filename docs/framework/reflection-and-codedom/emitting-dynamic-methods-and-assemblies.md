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
ms.openlocfilehash: 527da43807a0dbba8f5365c92f566053f10d49f5
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33848294"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="264a1-102">Generování dynamických metod a sestavení</span><span class="sxs-lookup"><span data-stu-id="264a1-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="264a1-103">Tato část popisuje sadu spravovaných typů v <xref:System.Reflection.Emit> obor názvů, který povolí kompilátoru nebo nástroj pro vydávání metadata a Microsoft (MSIL intermediate language) v době běhu a volitelně generovat soubor přenosné spustitelný soubor (PE) na disku.</span><span class="sxs-lookup"><span data-stu-id="264a1-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="264a1-104">Skriptovací stroje a kompilátory jsou primárními uživateli tohoto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="264a1-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="264a1-105">V této části, funkce poskytované <xref:System.Reflection.Emit> obor názvů se označuje jako reflexe emitování.</span><span class="sxs-lookup"><span data-stu-id="264a1-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="264a1-106">Emitování reflexe poskytuje následující možnosti:</span><span class="sxs-lookup"><span data-stu-id="264a1-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="264a1-107">Definovat zjednodušené globální metody na spuštění čas, pomocí <xref:System.Reflection.Emit.DynamicMethod> třídy a spouštět je použití delegátů.</span><span class="sxs-lookup"><span data-stu-id="264a1-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="264a1-108">Definování sestavení za běhu a jejich spuštění nebo je uložíte na disku.</span><span class="sxs-lookup"><span data-stu-id="264a1-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="264a1-109">Definovat sestavení za běhu, spustit, je uvolnit a povolit uvolňování, abyste získali zpět jejich prostředky.</span><span class="sxs-lookup"><span data-stu-id="264a1-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="264a1-110">Definování moduly v nové sestavení za běhu a spustit nebo je uložíte na disku.</span><span class="sxs-lookup"><span data-stu-id="264a1-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="264a1-111">Definování typů v modulech v době běhu, vytváření instancí těchto typů a vyvolání své metody.</span><span class="sxs-lookup"><span data-stu-id="264a1-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="264a1-112">Zadejte symbolické informace o definované moduly, které můžete používat nástroje, jako je ladicí programy a profilery kódu.</span><span class="sxs-lookup"><span data-stu-id="264a1-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="264a1-113">Kromě spravovaných typů v <xref:System.Reflection.Emit> obor názvů, existují rozhraní nespravované metadat, které jsou popsány v [rozhraní metadat](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) referenční dokumentace.</span><span class="sxs-lookup"><span data-stu-id="264a1-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="264a1-114">Emitování reflexe spravované poskytuje vyšší kontrolu sémantických chyb a na vyšší úrovni abstrakce metadat než rozhraní nespravované metadat.</span><span class="sxs-lookup"><span data-stu-id="264a1-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="264a1-115">Další užitečné prostředek pro práci s metadata a MSIL je dokumentace společné jazykové infrastruktury (CLI), zejména "Oddílu II: Metadata definice a sémantiku" a "Oddílu III: soubor CIL instrukce nastavení".</span><span class="sxs-lookup"><span data-stu-id="264a1-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="264a1-116">Dokumentace je k dispozici online na [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) a na [Ecma webu](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="264a1-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="264a1-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="264a1-117">In This Section</span></span>
  
[<span data-ttu-id="264a1-118">Bezpečnostní problémy v generování reflexe</span><span class="sxs-lookup"><span data-stu-id="264a1-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="264a1-119">Popisuje problémy související s vytvářením dynamické sestaveních pomocí reflexe emitování zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="264a1-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="264a1-120">[Postupy: definování a provádění dynamických metod](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="264a1-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="264a1-121">Ukazuje, jak provést jednoduchý dynamické metody a dynamické metoda vázaný na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="264a1-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="264a1-122">[Postupy: definování obecného typu pomocí reflexe emitování](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="264a1-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="264a1-123">Ukazuje, jak vytvořit jednoduché obecného typu se dva parametry typu, jak se má použít třídu rozhraní a zvláštní omezení pro parametry typu a postup vytvoření členy, které používají parametry typu třídy jako parametry a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="264a1-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="264a1-124">[Postupy: definování obecné metody pomocí reflexe emitování](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="264a1-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="264a1-125">Ukazuje, jak k vytváření, vydávání a vyvolání jednoduché obecná metoda.</span><span class="sxs-lookup"><span data-stu-id="264a1-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="264a1-126">[Collectible sestavení pro generování dynamickém typu](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="264a1-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="264a1-127">Představuje collectible sestavení, které jsou dynamická sestavení, které mohou být odpojen bez uvolnění domény aplikace, v jakém byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="264a1-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="264a1-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="264a1-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="264a1-129">Zařadí katalogu kódy MSIL instrukcí, které můžete použít k vytvoření těla metody.</span><span class="sxs-lookup"><span data-stu-id="264a1-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="264a1-130">Obsahuje spravované třídy používané k emitování dynamických metod a sestavení, typy.</span><span class="sxs-lookup"><span data-stu-id="264a1-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="264a1-131">Popisuje <xref:System.Type> třídy, která reprezentuje typy v spravované reflexe emitování reflexe a který je klíčová pro používání těchto technologií.</span><span class="sxs-lookup"><span data-stu-id="264a1-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="264a1-132">Obsahuje spravované třídy používané prozkoumat metadata a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="264a1-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="264a1-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="264a1-133">Related Sections</span></span>  
 [<span data-ttu-id="264a1-134">Reflexe</span><span class="sxs-lookup"><span data-stu-id="264a1-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="264a1-135">Vysvětluje, jak prozkoumat metadata a spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="264a1-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="264a1-136">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="264a1-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="264a1-137">Poskytuje přehled o sestavení v rozhraní .NET implementace.</span><span class="sxs-lookup"><span data-stu-id="264a1-137">Provides an overview of assemblies in .NET implementations.</span></span>
