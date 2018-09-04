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
ms.openlocfilehash: 955efad34f816cd0445c4ebdf120d8b614f0d351
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508519"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="ba679-102">Nespravované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ba679-102">Unmanaged API Reference</span></span>
<span data-ttu-id="ba679-103">Tato část obsahuje informace o nespravované rozhraní API, která je možné spravovat souvisejícím s kódem aplikace, jako je například hostitelská prostředí modulu runtime, kompilátory, disassemblery, obfuscators, ladicí programy a profilery.</span><span class="sxs-lookup"><span data-stu-id="ba679-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba679-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ba679-104">In This Section</span></span>  
 [<span data-ttu-id="ba679-105">Běžné typy dat</span><span class="sxs-lookup"><span data-stu-id="ba679-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="ba679-106">Uvádí běžné typy dat, které se používají, zejména v nespravované profilování a ladění v rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ba679-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="ba679-107">ALink</span><span class="sxs-lookup"><span data-stu-id="ba679-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="ba679-108">Popisuje rozhraní API ALink, který podporuje vytvoření nevázaného modulů a sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba679-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="ba679-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ba679-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="ba679-110">Podporuje modul vytváření a ověřování Authenticode XrML licence.</span><span class="sxs-lookup"><span data-stu-id="ba679-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="ba679-111">Konstanty</span><span class="sxs-lookup"><span data-stu-id="ba679-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="ba679-112">Popisuje, které jsou definovány v CorSym.idl konstanty.</span><span class="sxs-lookup"><span data-stu-id="ba679-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="ba679-113">Vlastní atributy rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba679-113">Custom Interface Attributes</span></span>](https://msdn.microsoft.com/library/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="ba679-114">Popisuje komponenty object model (COM) vlastní atributy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ba679-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="ba679-115">Ladění</span><span class="sxs-lookup"><span data-stu-id="ba679-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="ba679-116">Popisuje rozhraní API pro ladění, která umožňuje ladicí program k ladění kódu spuštěného v prostředí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ba679-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="ba679-117">Úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="ba679-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="ba679-118">Popisuje úložiště symbolů diagnostiky rozhraní API, která umožňuje kompilátoru generovat informace o symbolech pro použití ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="ba679-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="ba679-119">Fúze</span><span class="sxs-lookup"><span data-stu-id="ba679-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="ba679-120">Popisuje rozhraní API fusion, které umožňuje hostitelský modul runtime pro přístup k vlastnosti prostředků aplikace Pokud chcete najít správné verze prvků tyto prostředky pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ba679-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="ba679-121">Hostování</span><span class="sxs-lookup"><span data-stu-id="ba679-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="ba679-122">Popisuje hostujícího rozhraní API, která umožňuje nespravovaným hostitelům k integraci modulu CLR do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ba679-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="ba679-123">Metadata</span><span class="sxs-lookup"><span data-stu-id="ba679-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="ba679-124">Popisuje metadat rozhraní API, které umožňuje klientovi jako je například kompilátor generovat nebo získat přístup k metadatům komponenty bez typů načítání platformou CLR.</span><span class="sxs-lookup"><span data-stu-id="ba679-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="ba679-125">Profilace</span><span class="sxs-lookup"><span data-stu-id="ba679-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="ba679-126">Popisuje rozhraní profilování API umožňuje profileru sledujte provádění programu CLR.</span><span class="sxs-lookup"><span data-stu-id="ba679-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="ba679-127">Vytváření silných názvů</span><span class="sxs-lookup"><span data-stu-id="ba679-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="ba679-128">Popisuje silné pojmenovávání API, které umožňuje klientovi spravovat podepisování sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="ba679-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="ba679-129">WMI a čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="ba679-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="ba679-130">Popisuje rozhraní API, který obalují volání knihovny Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="ba679-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="ba679-131">Pomocné funkce Tlbexp</span><span class="sxs-lookup"><span data-stu-id="ba679-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="ba679-132">Popisuje dva pomocné funkce a rozhraní Exportér knihovny typů (Tlbexp.exe) během procesu převodu sestavení na typu knihovny.</span><span class="sxs-lookup"><span data-stu-id="ba679-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba679-133">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ba679-133">Related Sections</span></span>  
 [<span data-ttu-id="ba679-134">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="ba679-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="ba679-135">Rozšířené čtení pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ba679-135">Advanced Reading for the .NET Framework</span></span>](https://msdn.microsoft.com/library/faae8083-fecb-4514-b133-b0a5a32a7c3c)
