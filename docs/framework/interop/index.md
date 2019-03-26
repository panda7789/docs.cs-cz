---
title: Spolupráce s nespravovaným kódem
ms.date: 01/17/2018
helpviewer_keywords:
  - 'unmanaged code, interoperation'
  - 'managed code, interoperation with unmanaged code'
  - '.NET Framework, interoperation with unmanaged code'
  - unmanaged code
  - interoperation with unmanaged code
  - 'interoperation with unmanaged code, about interoperation'
  - 'components [.NET Framework], interoperation with unmanaged code'
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="00780-102">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="00780-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="00780-103">Rozhraní .NET Framework podporuje interakci s modelu COM komponenty modelu COM + služby, externí knihovny typů a řadě služeb operačního systému.</span><span class="sxs-lookup"><span data-stu-id="00780-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="00780-104">Datové typy, podpisy metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektové modely.</span><span class="sxs-lookup"><span data-stu-id="00780-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="00780-105">Pro zjednodušení spolupráce mezi komponenty rozhraní .NET Framework a nespravovaný kód a k usnadnění cesty migrace z klientů i serverů rozdíly mezi tyto modely objektů ukrývá modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="00780-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="00780-106">Kód, který spouští pod kontrolou modulu runtime se nazývá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="00780-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="00780-107">Kód, který běží mimo modul runtime a naopak, se nazývá nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="00780-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="00780-108">Komponenty modelu COM, ActiveX rozhraní a funkcí rozhraní API Windows jsou příkladem nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="00780-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="00780-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="00780-109">In this section</span></span>

[<span data-ttu-id="00780-110">Vystavení komponent COM pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00780-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="00780-111">Popisuje způsob použití komponent modelu COM z aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00780-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="00780-112">Vystavení komponent architektury .NET Framework pro COM</span><span class="sxs-lookup"><span data-stu-id="00780-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="00780-113">Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="00780-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="00780-114">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="00780-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="00780-115">Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.</span><span class="sxs-lookup"><span data-stu-id="00780-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="00780-116">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="00780-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="00780-117">Popisuje zařazování pro zprostředkovatele komunikace s objekty COM a platformu vyvolání.</span><span class="sxs-lookup"><span data-stu-id="00780-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="00780-118">Postupy: Mapování výsledků HRESULT a výjimek</span><span class="sxs-lookup"><span data-stu-id="00780-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="00780-119">Popisuje mapování mezi výjimky a HRESULT.</span><span class="sxs-lookup"><span data-stu-id="00780-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="00780-120">COM – obálky</span><span class="sxs-lookup"><span data-stu-id="00780-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="00780-121">Popisuje obálky poskytované komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="00780-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="00780-122">Ekvivalence typů a vestavěné typy spolupráce</span><span class="sxs-lookup"><span data-stu-id="00780-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="00780-123">Popisuje, jak se vloží informace o typu pro typy modelu COM v sestaveních a jak určuje ekvivalence vestavěné typy modelu COM, modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="00780-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="00780-124">Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="00780-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="00780-125">Popisuje, jak vytvořit primární sestavení vzájemné spolupráce pomocí *Tlbimp.exe* (Importér knihovny typů).</span><span class="sxs-lookup"><span data-stu-id="00780-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="00780-126">Postupy: Registrace primárních sestavení spolupráce</span><span class="sxs-lookup"><span data-stu-id="00780-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="00780-127">Popisuje postup registrace primárních sestavení spolupráce, než je můžete odkazovat ve svých projektech.</span><span class="sxs-lookup"><span data-stu-id="00780-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="00780-128">Bezregistrační zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="00780-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="00780-129">Popisuje, jak komunikace s objekty COM se může aktivovat komponenty bez pomocí registru Windows.</span><span class="sxs-lookup"><span data-stu-id="00780-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="00780-130">Postupy: Konfigurace Bezregistrační aktivace komponent COM založené na platformě .NET</span><span class="sxs-lookup"><span data-stu-id="00780-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="00780-131">Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložení manifestu do komponenty.</span><span class="sxs-lookup"><span data-stu-id="00780-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>
