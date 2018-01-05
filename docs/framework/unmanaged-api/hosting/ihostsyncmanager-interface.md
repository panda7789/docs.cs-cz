---
title: "IHostSyncManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="16851-102">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16851-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="16851-103">Poskytuje metody, které povolit modul CLR (CLR) k vytvoření synchronizace primitiv voláním hostitele místo použití funkce synchronizace Win32.</span><span class="sxs-lookup"><span data-stu-id="16851-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16851-104">Metody</span><span class="sxs-lookup"><span data-stu-id="16851-104">Methods</span></span>  
  
|<span data-ttu-id="16851-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="16851-105">Method</span></span>|<span data-ttu-id="16851-106">Popis</span><span class="sxs-lookup"><span data-stu-id="16851-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16851-107">CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="16851-108">Vytvoří objekt události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="16851-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="16851-109">CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="16851-110">Vytvoří objekt kritická sekce modulu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="16851-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="16851-111">CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="16851-112">Vytvoří objekt kritická sekce s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="16851-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="16851-113">CreateManualEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="16851-114">Vytvoří objekt Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="16851-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="16851-115">CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="16851-116">Vytvoří objekt monitorovanou událost automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="16851-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="16851-117">CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="16851-118">Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="16851-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="16851-119">CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="16851-120">Vytvoří objekt automatickým vynulováním událostí k provádění zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="16851-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="16851-121">CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="16851-122">Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objekt pro CLR, které chcete použít jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="16851-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="16851-123">SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="16851-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="16851-124">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="16851-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16851-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16851-125">Remarks</span></span>  
 <span data-ttu-id="16851-126">Modul CLR zjistí implementace hostitele `IHostSyncManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metoda s `IID` z IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="16851-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16851-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16851-127">Requirements</span></span>  
 <span data-ttu-id="16851-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16851-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16851-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16851-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16851-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16851-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16851-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16851-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16851-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="16851-132">See Also</span></span>  
 [<span data-ttu-id="16851-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16851-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="16851-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="16851-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
