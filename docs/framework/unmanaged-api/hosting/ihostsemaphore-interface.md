---
title: "IHostSemaphore – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore
helpviewer_keywords: IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcc6a9a7847932e9e469cdbffc9792e1d5860570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="9899b-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9899b-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="9899b-103">Představuje hostitele implementaci semaforu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="9899b-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9899b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9899b-104">Methods</span></span>  
  
|<span data-ttu-id="9899b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9899b-105">Method</span></span>|<span data-ttu-id="9899b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9899b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9899b-107">ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="9899b-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="9899b-108">Zvyšuje počet aktuální `IHostSemaphore` instanci zadanou velikost.</span><span class="sxs-lookup"><span data-stu-id="9899b-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="9899b-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="9899b-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="9899b-110">Způsobí, že aktuální `IHostSemaphore` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="9899b-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9899b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9899b-111">Requirements</span></span>  
 <span data-ttu-id="9899b-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9899b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9899b-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9899b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9899b-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9899b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9899b-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9899b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9899b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9899b-116">See Also</span></span>  
 [<span data-ttu-id="9899b-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9899b-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9899b-118">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9899b-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9899b-119">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9899b-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9899b-120">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9899b-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="9899b-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9899b-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
