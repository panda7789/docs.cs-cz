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
ms.openlocfilehash: 67b3225186f74fceadfb3104145743823ef82fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="5022c-102">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5022c-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="5022c-103">Představuje hostitele implementaci semaforu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="5022c-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5022c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5022c-104">Methods</span></span>  
  
|<span data-ttu-id="5022c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5022c-105">Method</span></span>|<span data-ttu-id="5022c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5022c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5022c-107">Releasesemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="5022c-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="5022c-108">Zvyšuje počet aktuální `IHostSemaphore` instanci zadanou velikost.</span><span class="sxs-lookup"><span data-stu-id="5022c-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="5022c-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="5022c-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="5022c-110">Způsobí, že aktuální `IHostSemaphore` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="5022c-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5022c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5022c-111">Requirements</span></span>  
 <span data-ttu-id="5022c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5022c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5022c-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5022c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5022c-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5022c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5022c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5022c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5022c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5022c-116">See Also</span></span>  
 [<span data-ttu-id="5022c-117">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5022c-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5022c-118">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5022c-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="5022c-119">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5022c-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="5022c-120">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5022c-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="5022c-121">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="5022c-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
