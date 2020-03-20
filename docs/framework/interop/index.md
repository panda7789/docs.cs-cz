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
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457966"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="4d8b0-102">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="4d8b0-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="4d8b0-103">Rozhraní .NET Framework podporuje interakci s komponentami modelu COM, službami modelu COM+, externími knihovnami typů a mnoha službami operačního systému.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="4d8b0-104">Datové typy, podpisy metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektovými modely.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="4d8b0-105">Chcete-li zjednodušit vzájemné spolupráce mezi součástmi rozhraní .NET Framework a nespravovaným kódem a usnadnit cestu migrace, soubor Runtime jazyka common jazyk ukrytý chod klientů i serverů rozdíly v těchto objektových modelech.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="4d8b0-106">Kód, který se spustí pod kontrolou runtime se nazývá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="4d8b0-107">Naopak kód, který běží mimo runtime se nazývá nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="4d8b0-108">Komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows jsou příklady nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4d8b0-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4d8b0-109">In this section</span></span>

[<span data-ttu-id="4d8b0-110">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d8b0-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="4d8b0-111">Popisuje způsob použití komponent modelu COM z aplikací rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="4d8b0-112">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="4d8b0-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="4d8b0-113">Popisuje způsob použití součástí rozhraní .NET Framework z aplikací modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="4d8b0-114">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="4d8b0-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="4d8b0-115">Popisuje, jak volat nespravované funkce dll pomocí platformy vyvolat.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="4d8b0-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="4d8b0-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="4d8b0-117">Popisuje zařazování pro interop com a platformy invoke.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="4d8b0-118">Postupy: Mapování výsledků HRESULT a výjimek</span><span class="sxs-lookup"><span data-stu-id="4d8b0-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="4d8b0-119">Popisuje mapování mezi výjimkami a HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="4d8b0-120">Ekvivalence typů a vestavěné typy spolupráce</span><span class="sxs-lookup"><span data-stu-id="4d8b0-120">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="4d8b0-121">Popisuje, jak jsou informace o typu pro typy COM vloženy do sestavení a jak běžný jazyk runtime určuje rovnocennost vložených typů COM.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-121">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="4d8b0-122">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="4d8b0-122">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="4d8b0-123">Popisuje, jak vytvořit primární interop sestavení pomocí *Tlbimp.exe* (Import knihovny typů).</span><span class="sxs-lookup"><span data-stu-id="4d8b0-123">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="4d8b0-124">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="4d8b0-124">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="4d8b0-125">Popisuje, jak zaregistrovat primární sestavení interop před odkazem na ně v projektech.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-125">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="4d8b0-126">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="4d8b0-126">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="4d8b0-127">Popisuje, jak může interop modelu COM aktivovat součásti bez použití registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-127">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="4d8b0-128">Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d8b0-128">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="4d8b0-129">Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložit manifest komponenty.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-129">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="4d8b0-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4d8b0-130">Related sections</span></span>

[<span data-ttu-id="4d8b0-131">Obálky COM</span><span class="sxs-lookup"><span data-stu-id="4d8b0-131">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="4d8b0-132">Popisuje obálky poskytované com interop.</span><span class="sxs-lookup"><span data-stu-id="4d8b0-132">Describes the wrappers provided by COM interop.</span></span>
