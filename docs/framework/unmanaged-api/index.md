---
title: "Nespravované rozhraní API"
ms.custom: 
ms.date: 11/06/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9836d8d02bb81fc19a5b3a1714e32fcefeb8791d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="82ae8-102">Nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="82ae8-102">Unmanaged API Reference</span></span>
<span data-ttu-id="82ae8-103">Tato část obsahuje informace o nespravovaného rozhraní API, které je možné spravovat-související s kódem aplikace, jako je modulu runtime, kompilátory, disassemblers, obfuscators, ladicí programy a profilery.</span><span class="sxs-lookup"><span data-stu-id="82ae8-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82ae8-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="82ae8-104">In This Section</span></span>  
 [<span data-ttu-id="82ae8-105">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="82ae8-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="82ae8-106">Jsou uvedeny běžné typy dat, které se používají, zejména v nespravované profilování a ladění v rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="82ae8-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="82ae8-107">ALink</span><span class="sxs-lookup"><span data-stu-id="82ae8-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="82ae8-108">Popisuje rozhraní API ALink, které podporuje vytváření sestavení rozhraní .NET Framework a nevázaný moduly.</span><span class="sxs-lookup"><span data-stu-id="82ae8-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="82ae8-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="82ae8-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="82ae8-110">Podporuje modul vytvoření a ověření Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="82ae8-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="82ae8-111">Konstanty</span><span class="sxs-lookup"><span data-stu-id="82ae8-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="82ae8-112">Popisuje konstanty, které jsou definovány v CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="82ae8-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="82ae8-113">Vlastní rozhraní atributy</span><span class="sxs-lookup"><span data-stu-id="82ae8-113">Custom Interface Attributes</span></span>](http://msdn.microsoft.com/en-us/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="82ae8-114">Popisuje component object model (COM) vlastní rozhraní atributy.</span><span class="sxs-lookup"><span data-stu-id="82ae8-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="82ae8-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="82ae8-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="82ae8-116">Popisuje ladění rozhraní API, které umožňuje ladicí program k ladění kódu, který běží v prostředí běžné language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="82ae8-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="82ae8-117">Úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="82ae8-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="82ae8-118">Popisuje úložiště symbolů diagnostiky rozhraní API, která umožňuje kompilátoru ke generování informací o symbolu za účelem použití ladicí program.</span><span class="sxs-lookup"><span data-stu-id="82ae8-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="82ae8-119">Fúze</span><span class="sxs-lookup"><span data-stu-id="82ae8-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="82ae8-120">Popisuje rozhraní API fusion, která umožňuje hostitele modulu runtime pro přístup k vlastnostem prostředky aplikace, aby bylo možné najít správnou verzí tyto prostředky pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="82ae8-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="82ae8-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="82ae8-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="82ae8-122">Popisuje hostování rozhraní API, které umožňuje nespravované hostitelům integraci modulu CLR do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="82ae8-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="82ae8-123">Metadata</span><span class="sxs-lookup"><span data-stu-id="82ae8-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="82ae8-124">Popisuje metadat rozhraní API, které umožňuje klientovi například kompilátor ke generování nebo získat přístup k metadatům komponenty bez typy načítá pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="82ae8-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="82ae8-125">Profilace</span><span class="sxs-lookup"><span data-stu-id="82ae8-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="82ae8-126">Popisuje profilování rozhraní API, které umožňuje profileru ke sledování provádění programu pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="82ae8-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="82ae8-127">Vytváření silných názvů</span><span class="sxs-lookup"><span data-stu-id="82ae8-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="82ae8-128">Popisuje silné pojmenování API, která umožňuje klientovi ke správě podepsání sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="82ae8-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="82ae8-129">WMI a čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="82ae8-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="82ae8-130">Popisuje rozhraní API, která zabalení volání knihovny Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="82ae8-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="82ae8-131">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="82ae8-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="82ae8-132">Popisuje dvou pomocných funkcí a rozhraní používá Exportér knihovny typů (Tlbexp.exe) během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="82ae8-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82ae8-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="82ae8-133">Related Sections</span></span>  
 [<span data-ttu-id="82ae8-134">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="82ae8-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="82ae8-135">Pokročilé čtení pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="82ae8-135">Advanced Reading for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)
