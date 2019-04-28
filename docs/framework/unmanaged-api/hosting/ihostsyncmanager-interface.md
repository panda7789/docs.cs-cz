---
title: IHostSyncManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769626"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="21e36-102">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e36-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="21e36-103">Poskytuje metody, které umožňují common language runtime (CLR) k vytvoření synchronizací primitiv voláním hostitele namísto použití funkce synchronizace Win32.</span><span class="sxs-lookup"><span data-stu-id="21e36-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21e36-104">Metody</span><span class="sxs-lookup"><span data-stu-id="21e36-104">Methods</span></span>  
  
|<span data-ttu-id="21e36-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-105">Method</span></span>|<span data-ttu-id="21e36-106">Popis</span><span class="sxs-lookup"><span data-stu-id="21e36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21e36-107">CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="21e36-108">Vytvoří objekt události automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="21e36-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="21e36-109">CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="21e36-110">Vytvoří objekt kritický oddíl pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="21e36-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="21e36-111">CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="21e36-112">Vytvoří objekt kritický oddíl s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="21e36-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="21e36-113">CreateManualEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="21e36-114">Vytvoří objekt ruční obnovení události.</span><span class="sxs-lookup"><span data-stu-id="21e36-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="21e36-115">CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="21e36-116">Vytvoří objekt monitorovanou událost automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="21e36-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="21e36-117">CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="21e36-118">Vytvoří objekt ruční obnovení události pro implementaci zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="21e36-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="21e36-119">CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="21e36-120">Vytvoří objekt automatického resetu pro provádění zapisovací zámek.</span><span class="sxs-lookup"><span data-stu-id="21e36-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="21e36-121">CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="21e36-122">Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objektu pro modul CLR, který chcete použít jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="21e36-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="21e36-123">SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="21e36-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="21e36-124">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instanci přidružit s aktuálním `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="21e36-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e36-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21e36-125">Remarks</span></span>  
 <span data-ttu-id="21e36-126">Modul CLR zjistí hostitele provádění `IHostSyncManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metodou `IID` z IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="21e36-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e36-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21e36-127">Requirements</span></span>  
 <span data-ttu-id="21e36-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e36-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e36-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21e36-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21e36-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21e36-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21e36-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e36-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e36-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21e36-132">See also</span></span>

- [<span data-ttu-id="21e36-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="21e36-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="21e36-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="21e36-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
