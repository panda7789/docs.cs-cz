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
ms.openlocfilehash: 2cf490bcd167b7a498ae21f479f616694ccb5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139477"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="b96c6-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96c6-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="b96c6-103">Představuje implementaci semaforu pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="b96c6-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b96c6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b96c6-104">Methods</span></span>  
  
|<span data-ttu-id="b96c6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b96c6-105">Method</span></span>|<span data-ttu-id="b96c6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b96c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b96c6-107">ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="b96c6-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="b96c6-108">Zvýší počet aktuálních instancí `IHostSemaphore` o zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b96c6-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="b96c6-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="b96c6-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="b96c6-110">Způsobí, že aktuální instance `IHostSemaphore` počká, dokud ji nevlastníte, nebo dokud neuplyne zadaný čas.</span><span class="sxs-lookup"><span data-stu-id="b96c6-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b96c6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b96c6-111">Requirements</span></span>  
 <span data-ttu-id="b96c6-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b96c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96c6-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b96c6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b96c6-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b96c6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b96c6-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b96c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96c6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b96c6-116">See also</span></span>

- [<span data-ttu-id="b96c6-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96c6-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b96c6-118">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96c6-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="b96c6-119">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96c6-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="b96c6-120">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b96c6-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="b96c6-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b96c6-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
