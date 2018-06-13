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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389504"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="fd09b-102">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="fd09b-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="fd09b-103">Rozhraní .NET Framework zvýší úroveň interakci s COM komponenty modelu COM + služby, knihovny externích typů a mnoho služeb operačního systému.</span><span class="sxs-lookup"><span data-stu-id="fd09b-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="fd09b-104">Datové typy, metoda podpisy a zpracování chyb mechanismy liší mezi spravovanými a nespravovanými objektové modely.</span><span class="sxs-lookup"><span data-stu-id="fd09b-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="fd09b-105">Pro zjednodušení vzájemná spolupráce mezi součástmi rozhraní .NET Framework a nespravovaného kódu a usnadňují cesty migrace, modul common language runtime ukrývá od klientů a serverů rozdíly v těchto modelů objektu.</span><span class="sxs-lookup"><span data-stu-id="fd09b-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="fd09b-106">Kód, který spouští pod kontrolou modulu runtime nazývá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fd09b-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="fd09b-107">Kód, který je spuštěn mimo modul runtime naopak se nazývá nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fd09b-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="fd09b-108">COM – součásti ActiveX rozhraní a funkcí rozhraní API Win32 jsou příklady nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="fd09b-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fd09b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fd09b-109">In this section</span></span>

[<span data-ttu-id="fd09b-110">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd09b-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="fd09b-111">Popisuje, jak komponenty modelu COM v aplikacích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd09b-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="fd09b-112">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="fd09b-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="fd09b-113">Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="fd09b-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="fd09b-114">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="fd09b-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="fd09b-115">Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="fd09b-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="fd09b-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="fd09b-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="fd09b-117">Popisuje zařazování pro vyvolání zprostředkovatel komunikace s objekty COM a platformu.</span><span class="sxs-lookup"><span data-stu-id="fd09b-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="fd09b-118">Postupy: Mapování výsledků HRESULT a výjimek</span><span class="sxs-lookup"><span data-stu-id="fd09b-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="fd09b-119">Popisuje mapování mezi výjimky a jejich hodnoty HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fd09b-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="fd09b-120">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="fd09b-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="fd09b-121">Popisuje obálky poskytované zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="fd09b-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="fd09b-122">Ekvivalence typů a vestavěné typy spolupráce</span><span class="sxs-lookup"><span data-stu-id="fd09b-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="fd09b-123">Popisuje, jak vložené informací o typu pro typy modelu COM v sestavení a určuje, jak modul common language runtime ekvivalence typů vložených COM.</span><span class="sxs-lookup"><span data-stu-id="fd09b-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="fd09b-124">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="fd09b-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="fd09b-125">Popisuje, jak vytvořit primární spolupracující sestavení pomocí *Tlbimp.exe* (Importér knihovny).</span><span class="sxs-lookup"><span data-stu-id="fd09b-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="fd09b-126">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="fd09b-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="fd09b-127">Popisuje postup registrace primárních sestavení vzájemné spolupráce, než je můžete odkazovat ve vašich projektů.</span><span class="sxs-lookup"><span data-stu-id="fd09b-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="fd09b-128">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="fd09b-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="fd09b-129">Popisuje, jak zprostředkovatel komunikace s objekty COM součásti aktivovat bez použití registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fd09b-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="fd09b-130">Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fd09b-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="fd09b-131">Popisuje postup vytvoření manifest aplikace a jak vytvořit a vložení manifestu součástí.</span><span class="sxs-lookup"><span data-stu-id="fd09b-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
