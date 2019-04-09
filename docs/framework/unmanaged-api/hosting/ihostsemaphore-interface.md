---
title: IHostSemaphore – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d7d4a295832a958fb6a8fe2e6c43a09135500d3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182283"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="e19ec-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19ec-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="e19ec-103">Představuje hostitele implementaci semaforu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="e19ec-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e19ec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e19ec-104">Methods</span></span>  
  
|<span data-ttu-id="e19ec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e19ec-105">Method</span></span>|<span data-ttu-id="e19ec-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e19ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e19ec-107">ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="e19ec-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="e19ec-108">Zvýší počet aktuální `IHostSemaphore` instance podle zadaného množství.</span><span class="sxs-lookup"><span data-stu-id="e19ec-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="e19ec-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="e19ec-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="e19ec-110">Způsobí, že aktuální `IHostSemaphore` instance počkat, dokud je ve vlastnictví nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="e19ec-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e19ec-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e19ec-111">Requirements</span></span>  
 <span data-ttu-id="e19ec-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e19ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e19ec-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e19ec-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e19ec-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e19ec-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e19ec-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e19ec-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e19ec-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e19ec-116">See also</span></span>

- [<span data-ttu-id="e19ec-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19ec-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e19ec-118">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19ec-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e19ec-119">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19ec-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e19ec-120">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e19ec-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="e19ec-121">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="e19ec-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
