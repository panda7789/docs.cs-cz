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
ms.openlocfilehash: 8345d85502087568cb05dd262cccf181e3ca07ac
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803692"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="1448f-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1448f-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="1448f-103">Představuje implementaci semaforu pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="1448f-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1448f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1448f-104">Methods</span></span>  
  
|<span data-ttu-id="1448f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1448f-105">Method</span></span>|<span data-ttu-id="1448f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1448f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1448f-107">ReleaseSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="1448f-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="1448f-108">Zvýší počet aktuálních `IHostSemaphore` instancí o zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1448f-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="1448f-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="1448f-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="1448f-110">Způsobí, že aktuální `IHostSemaphore` instance počká, dokud je nevlastní nebo zadaná doba uplynula.</span><span class="sxs-lookup"><span data-stu-id="1448f-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1448f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1448f-111">Requirements</span></span>  
 <span data-ttu-id="1448f-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1448f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1448f-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1448f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1448f-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1448f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1448f-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1448f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1448f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1448f-116">See also</span></span>

- [<span data-ttu-id="1448f-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1448f-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1448f-118">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1448f-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="1448f-119">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1448f-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="1448f-120">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1448f-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="1448f-121">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1448f-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
