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
ms.openlocfilehash: 103deb5ec46ba8c1d385c5339bc52a0c220c4c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439765"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="5a465-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a465-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="5a465-103">Představuje hostitele implementaci semaforu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="5a465-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a465-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a465-104">Methods</span></span>  
  
|<span data-ttu-id="5a465-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a465-105">Method</span></span>|<span data-ttu-id="5a465-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5a465-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a465-107">ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="5a465-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="5a465-108">Zvyšuje počet aktuální `IHostSemaphore` instanci zadanou velikost.</span><span class="sxs-lookup"><span data-stu-id="5a465-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="5a465-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="5a465-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="5a465-110">Způsobí, že aktuální `IHostSemaphore` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="5a465-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a465-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a465-111">Requirements</span></span>  
 <span data-ttu-id="5a465-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a465-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a465-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a465-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a465-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a465-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a465-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a465-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a465-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a465-116">See Also</span></span>  
 [<span data-ttu-id="5a465-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a465-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5a465-118">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a465-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="5a465-119">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a465-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="5a465-120">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a465-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="5a465-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5a465-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
