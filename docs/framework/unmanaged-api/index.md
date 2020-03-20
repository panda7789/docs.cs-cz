---
title: Nespravované rozhraní API
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: f7dd78b889129998dee31a22f5dd23325613b8ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73092018"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="64161-102">Nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="64161-102">Unmanaged API Reference</span></span>
<span data-ttu-id="64161-103">Tato část obsahuje informace o nespravovaných api, které mohou být použity aplikace související se spravovaným kódem, jako jsou například runtime hostitelé, kompilátory, rozklady, obfuscators, ladicí programy a profilovací programy.</span><span class="sxs-lookup"><span data-stu-id="64161-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64161-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="64161-104">In This Section</span></span>  
 [<span data-ttu-id="64161-105">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="64161-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="64161-106">Uvádí běžné datové typy, které se používají, zejména v nespravované profilování a ladění api.</span><span class="sxs-lookup"><span data-stu-id="64161-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="64161-107">ALink</span><span class="sxs-lookup"><span data-stu-id="64161-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="64161-108">Popisuje rozhraní ALink API, které podporuje vytváření sestavení rozhraní .NET Framework a nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="64161-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="64161-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="64161-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="64161-110">Podporuje modul pro vytváření a ověřování licencí Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="64161-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="64161-111">Konstanty</span><span class="sxs-lookup"><span data-stu-id="64161-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="64161-112">Popisuje konstanty, které jsou definovány v CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="64161-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="64161-113">[Vlastní atributy rozhraní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64161-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="64161-114">Popisuje vlastní atributy rozhraní modelu COM (COMPONENT Object Model).</span><span class="sxs-lookup"><span data-stu-id="64161-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="64161-115">ladění</span><span class="sxs-lookup"><span data-stu-id="64161-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="64161-116">Popisuje ladění rozhraní API, který umožňuje ladicí program ladit kód, který běží v prostředí CLR (COMMON Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="64161-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="64161-117">Úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="64161-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="64161-118">Popisuje rozhraní API úložiště symbolů diagnostiky, které umožňuje kompilátoru generovat informace o symbolech pro použití ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="64161-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="64161-119">Fúze</span><span class="sxs-lookup"><span data-stu-id="64161-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="64161-120">Popisuje rozhraní API pro fúzi, které umožňuje hostiteli runtime přístup k vlastnostem prostředků aplikace za účelem vyhledání správných verzí těchto prostředků pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="64161-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="64161-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="64161-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="64161-122">Popisuje hostitelské rozhraní API, které umožňuje nespravovaným hostitelům integrovat CLR do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="64161-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="64161-123">Metadata</span><span class="sxs-lookup"><span data-stu-id="64161-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="64161-124">Popisuje rozhraní API metadat, které umožňuje klientovi, jako je například kompilátor generovat nebo přistupovat k metadatům komponenty bez typů načtených clr.</span><span class="sxs-lookup"><span data-stu-id="64161-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="64161-125">Profilování</span><span class="sxs-lookup"><span data-stu-id="64161-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="64161-126">Popisuje profilování rozhraní API, který umožňuje profiler sledovat spuštění programu clr.</span><span class="sxs-lookup"><span data-stu-id="64161-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="64161-127">Silné pojmenování</span><span class="sxs-lookup"><span data-stu-id="64161-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="64161-128">Popisuje silné pojmenování rozhraní API, které umožňuje klientovi spravovat silné podepisování názvů pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="64161-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="64161-129">WMI a čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="64161-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="64161-130">Popisuje api, která zalamují volání knihoven WMI (WMI) systému Windows.</span><span class="sxs-lookup"><span data-stu-id="64161-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="64161-131">Podpůrné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="64161-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="64161-132">Popisuje dvě pomocné funkce a rozhraní používané exportérem knihovny typů (Tlbexp.exe) během procesu převodu knihovny typu sestavení.</span><span class="sxs-lookup"><span data-stu-id="64161-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="64161-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="64161-133">Related Sections</span></span>  
 [<span data-ttu-id="64161-134">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="64161-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
