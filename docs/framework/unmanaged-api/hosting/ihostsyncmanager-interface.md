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
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132632"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="ede4c-102">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede4c-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="ede4c-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) vytvářet primitivy synchronizace voláním hostitele namísto použití synchronizačních funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="ede4c-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ede4c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ede4c-104">Methods</span></span>  
  
|<span data-ttu-id="ede4c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-105">Method</span></span>|<span data-ttu-id="ede4c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ede4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ede4c-107">CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="ede4c-108">Vytvoří objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="ede4c-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="ede4c-109">CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="ede4c-110">Vytvoří objekt kritického oddílu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="ede4c-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="ede4c-111">CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="ede4c-112">Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="ede4c-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="ede4c-113">CreateManualEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="ede4c-114">Vytvoří objekt události ručního resetování.</span><span class="sxs-lookup"><span data-stu-id="ede4c-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="ede4c-115">CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="ede4c-116">Vytvoří monitorovaný objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="ede4c-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="ede4c-117">CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="ede4c-118">Vytvoří objekt události ručního resetování pro implementaci zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="ede4c-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="ede4c-119">CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="ede4c-120">Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="ede4c-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="ede4c-121">CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="ede4c-122">Vytvoří objekt [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) pro CLR, který se použije jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="ede4c-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="ede4c-123">SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="ede4c-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="ede4c-124">Nastaví instanci [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) k přidružení k aktuální instanci `IHostSyncManager`.</span><span class="sxs-lookup"><span data-stu-id="ede4c-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede4c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ede4c-125">Remarks</span></span>  
 <span data-ttu-id="ede4c-126">Modul CLR zjistí implementaci `IHostSyncManager` hostitele voláním metody [IHostControl:: GetHostManager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) s `IID` IID_IHostSyncManager.</span><span class="sxs-lookup"><span data-stu-id="ede4c-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede4c-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ede4c-127">Requirements</span></span>  
 <span data-ttu-id="ede4c-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede4c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede4c-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ede4c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ede4c-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ede4c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ede4c-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede4c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede4c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ede4c-132">See also</span></span>

- [<span data-ttu-id="ede4c-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ede4c-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ede4c-134">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ede4c-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
