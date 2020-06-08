---
title: IGCHost – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 6b6f2dbaa49c29f6614e9c39a3f408d4d1453983
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501622"
---
# <a name="igchost-interface"></a><span data-ttu-id="5bd7a-102">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5bd7a-102">IGCHost Interface</span></span>
<span data-ttu-id="5bd7a-103">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bd7a-104">Počínaje .NET Framework 4,5 lze pomocí metody [IGCHost2 –:: SetGCStartupLimitsEx –](igchost2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší, než je `DWORD` limit, který je určen metodou [SetGCStartupLimits –](igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5bd7a-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bd7a-105">Toto rozhraní je jenom pro odborné použití.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-105">This interface is for expert usage only.</span></span> <span data-ttu-id="5bd7a-106">Může ovlivnit výkon aplikace, pokud se používá nesprávně.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5bd7a-107">Metody</span><span class="sxs-lookup"><span data-stu-id="5bd7a-107">Methods</span></span>  
  
|<span data-ttu-id="5bd7a-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-108">Method</span></span>|<span data-ttu-id="5bd7a-109">Description</span><span class="sxs-lookup"><span data-stu-id="5bd7a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bd7a-110">Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="5bd7a-111">Vynutí, aby se kolekce stala pro danou generaci, bez ohledu na stav aktuálního uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="5bd7a-112">GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="5bd7a-113">Získá statistiku pro aktuální stav systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="5bd7a-114">GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="5bd7a-115">Načte statistiku jednotlivých vláken pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="5bd7a-116">SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="5bd7a-117">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="5bd7a-118">SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="5bd7a-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="5bd7a-119">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5bd7a-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bd7a-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bd7a-120">Requirements</span></span>  
 <span data-ttu-id="5bd7a-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bd7a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd7a-122">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="5bd7a-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5bd7a-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5bd7a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bd7a-124">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd7a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd7a-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bd7a-125">See also</span></span>

- [<span data-ttu-id="5bd7a-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5bd7a-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="5bd7a-127">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="5bd7a-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
