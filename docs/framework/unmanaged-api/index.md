---
title: Nespravované rozhraní API
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677bee7319a80e405098f0dd5c8684765806c5f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796883"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="7d164-102">Nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7d164-102">Unmanaged API Reference</span></span>
<span data-ttu-id="7d164-103">Tato část obsahuje informace o nespravovaných rozhraních API, která mohou používat aplikace související se spravovaným kódem, jako jsou hostitelé modulu runtime, kompilátory, rozdávající, deassemblery, ladicí programy a profilery.</span><span class="sxs-lookup"><span data-stu-id="7d164-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d164-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7d164-104">In This Section</span></span>  
 [<span data-ttu-id="7d164-105">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="7d164-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="7d164-106">Obsahuje seznam běžných používaných datových typů, zejména v nespravovaných profilech a rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="7d164-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="7d164-107">ALink</span><span class="sxs-lookup"><span data-stu-id="7d164-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="7d164-108">Popisuje rozhraní API ALink, které podporuje vytváření .NET Framework sestavení a nevázaných modulů.</span><span class="sxs-lookup"><span data-stu-id="7d164-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="7d164-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="7d164-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="7d164-110">Podporuje modul pro vytváření a ověřování licencí Authenticode.</span><span class="sxs-lookup"><span data-stu-id="7d164-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="7d164-111">Konstanty</span><span class="sxs-lookup"><span data-stu-id="7d164-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="7d164-112">Popisuje konstanty, které jsou definovány v CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="7d164-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="7d164-113">[Vlastní atributy rozhraní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7d164-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="7d164-114">Popisuje vlastní atributy rozhraní modelu COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="7d164-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="7d164-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="7d164-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="7d164-116">Popisuje rozhraní API pro ladění, které umožňuje ladicímu programu ladit kód, který běží v prostředí modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7d164-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="7d164-117">Úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="7d164-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="7d164-118">Popisuje rozhraní API pro úložiště symbolů diagnostiky, které umožňuje kompilátoru generovat informace o symbolech pro použití v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="7d164-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="7d164-119">Fúze</span><span class="sxs-lookup"><span data-stu-id="7d164-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="7d164-120">Popisuje rozhraní API pro syntézu, které umožňuje hostiteli modulu runtime získat přístup k vlastnostem prostředků aplikace, aby bylo možné najít správné verze těchto prostředků pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d164-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="7d164-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="7d164-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="7d164-122">Popisuje hostující rozhraní API, které umožňuje nespravovaným hostitelům integrovat CLR do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="7d164-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="7d164-123">Metadata</span><span class="sxs-lookup"><span data-stu-id="7d164-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="7d164-124">Popisuje rozhraní API metadat, které umožňuje klientovi, jako je například kompilátor, generovat nebo přistupovat k metadatům komponenty bez typů načítaných modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="7d164-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="7d164-125">Profilace</span><span class="sxs-lookup"><span data-stu-id="7d164-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="7d164-126">Popisuje rozhraní API profilování, které umožňuje profileru monitorovat provádění programu modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="7d164-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="7d164-127">Vytváření silných názvů</span><span class="sxs-lookup"><span data-stu-id="7d164-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="7d164-128">Popisuje rozhraní API pro silné pojmenování, které umožňuje klientovi spravovat podepisování silného názvu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d164-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="7d164-129">WMI a čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="7d164-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="7d164-130">Popisuje rozhraní API, která zabalí volání do knihoven rozhraní WMI (Windows Management Instrumentation) (WMI).</span><span class="sxs-lookup"><span data-stu-id="7d164-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="7d164-131">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="7d164-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="7d164-132">V této části najdete popis dvou pomocných funkcí a rozhraní, které používá Exportér knihovny typů (Tlbexp. exe) během procesu převodu sestavení na typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="7d164-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d164-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7d164-133">Related Sections</span></span>  
 [<span data-ttu-id="7d164-134">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="7d164-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
