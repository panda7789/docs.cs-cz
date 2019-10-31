---
title: Spolupráce s nespravovaným kódem
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: cdd8d2781331956289d2b74162e653ba1ee8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114230"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="81305-102">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="81305-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="81305-103">.NET Framework podporuje interakci s komponentami COM, službami COM+, externími knihovnami typů a mnoha službami operačního systému.</span><span class="sxs-lookup"><span data-stu-id="81305-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="81305-104">Datové typy, signatury metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektovými modely.</span><span class="sxs-lookup"><span data-stu-id="81305-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="81305-105">Aby bylo možné zjednodušit vzájemnou spolupráci mezi .NET Framework komponentami a nespravovaným kódem, a usnadnit tak cestu migrace, modul CLR (Common Language Runtime) se v těchto objektových modelech skrývá mezi klienty a servery.</span><span class="sxs-lookup"><span data-stu-id="81305-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="81305-106">Kód, který se spouští pod ovládacím prvkem modulu runtime, se nazývá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="81305-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="81305-107">Naopak kód, který se spouští mimo modul runtime, se nazývá nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="81305-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="81305-108">Mezi příklady nespravovaného kódu patří komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="81305-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="81305-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="81305-109">In this section</span></span>

[<span data-ttu-id="81305-110">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81305-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="81305-111">Popisuje, jak použít komponenty modelu COM z aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81305-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="81305-112">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="81305-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="81305-113">Popisuje, jak používat .NET Framework komponenty z aplikací modelu COM.</span><span class="sxs-lookup"><span data-stu-id="81305-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="81305-114">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="81305-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="81305-115">Popisuje, jak volat nespravované funkce knihovny DLL pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="81305-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="81305-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="81305-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="81305-117">Popisuje zařazování pro zprostředkovatele komunikace s objekty COM a vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="81305-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="81305-118">Postupy: Mapování výsledků HRESULT a výjimek</span><span class="sxs-lookup"><span data-stu-id="81305-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="81305-119">Popisuje mapování mezi výjimkami a HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="81305-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="81305-120">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="81305-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="81305-121">Popisuje obálky poskytované zprostředkovatelem komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="81305-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="81305-122">Ekvivalence typů a vestavěné typy spolupráce</span><span class="sxs-lookup"><span data-stu-id="81305-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="81305-123">Popisuje způsob vložení informací o typu pro typy modelu COM do sestavení a jak modul CLR (Common Language Runtime) určí rovnocennost integrovaných typů COM.</span><span class="sxs-lookup"><span data-stu-id="81305-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="81305-124">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="81305-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="81305-125">Popisuje, jak vypracovávat primární spolupracující sestavení pomocí nástroje *Tlbimp. exe* (importér knihovny typů).</span><span class="sxs-lookup"><span data-stu-id="81305-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="81305-126">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="81305-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="81305-127">Popisuje, jak registrovat primární sestavení vzájemné spolupráce předtím, než na ně můžete odkazovat v projektech.</span><span class="sxs-lookup"><span data-stu-id="81305-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="81305-128">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="81305-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="81305-129">Popisuje, jak může zprostředkovatel komunikace s objekty COM aktivovat součásti bez použití registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="81305-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="81305-130">Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81305-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="81305-131">Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložit manifest součásti.</span><span class="sxs-lookup"><span data-stu-id="81305-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
