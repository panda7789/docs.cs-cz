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
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="99410-102">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99410-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="99410-103">Poskytuje metody, které povolit modul CLR (CLR) k vytvoření synchronizace primitiv voláním hostitele místo použití funkce synchronizace Win32.</span><span class="sxs-lookup"><span data-stu-id="99410-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99410-104">Metody</span><span class="sxs-lookup"><span data-stu-id="99410-104">Methods</span></span>  
  
|<span data-ttu-id="99410-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="99410-105">Method</span></span>|<span data-ttu-id="99410-106">Popis</span><span class="sxs-lookup"><span data-stu-id="99410-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99410-107">Createautoevent – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="99410-108">Vytvoří objekt události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="99410-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="99410-109">Createcrst – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="99410-110">Vytvoří objekt kritická sekce modulu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="99410-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="99410-111">Createcrstwithspincount – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="99410-112">Vytvoří objekt kritická sekce s počtem typu číselník pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="99410-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="99410-113">Createmanualevent – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="99410-114">Vytvoří objekt Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="99410-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="99410-115">Createmonitorevent – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="99410-116">Vytvoří objekt monitorovanou událost automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="99410-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="99410-117">Createrwlockreaderevent – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="99410-118">Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="99410-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="99410-119">Createrwlockwriterevent – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="99410-120">Vytvoří objekt automatickým vynulováním událostí k provádění zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="99410-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="99410-121">Createsemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="99410-122">Vytvoří [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) objekt pro CLR, které chcete použít jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="99410-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="99410-123">Setclrsyncmanager – metoda</span><span class="sxs-lookup"><span data-stu-id="99410-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="99410-124">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="99410-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99410-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99410-125">Remarks</span></span>  
 <span data-ttu-id="99410-126">Modul CLR zjistí implementace hostitele `IHostSyncManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metoda s `IID` z IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="99410-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99410-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99410-127">Requirements</span></span>  
 <span data-ttu-id="99410-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99410-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99410-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99410-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99410-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99410-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99410-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99410-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99410-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="99410-132">See Also</span></span>  
 [<span data-ttu-id="99410-133">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99410-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="99410-134">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="99410-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
