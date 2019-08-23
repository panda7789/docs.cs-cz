---
title: IHostGCManager::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb78026f875c18a557951108518c9280f5eb567d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937683"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="2a01c-102">IHostGCManager::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="2a01c-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="2a01c-103">Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2a01c-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a01c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a01c-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a01c-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2a01c-105">Return Value</span></span>  
  
|<span data-ttu-id="2a01c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a01c-106">HRESULT</span></span>|<span data-ttu-id="2a01c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a01c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a01c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a01c-108">S_OK</span></span>|<span data-ttu-id="2a01c-109">`ThreadIsBlockingForSuspension`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2a01c-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="2a01c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2a01c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2a01c-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2a01c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2a01c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2a01c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2a01c-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2a01c-113">The call timed out.</span></span>|  
|<span data-ttu-id="2a01c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2a01c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2a01c-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2a01c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2a01c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2a01c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2a01c-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2a01c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2a01c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2a01c-118">E_FAIL</span></span>|<span data-ttu-id="2a01c-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2a01c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2a01c-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2a01c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2a01c-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2a01c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a01c-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a01c-122">Remarks</span></span>  
 <span data-ttu-id="2a01c-123">Modul CLR obvykle volá `ThreadIsBlockForSuspension` metodu v přípravě na uvolňování paměti, aby hostitel měl možnost znovu naplánovat vlákno pro nespravované úlohy.</span><span class="sxs-lookup"><span data-stu-id="2a01c-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2a01c-124">Hostitel může znovu naplánovat úlohy až po volání `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="2a01c-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="2a01c-125">Po volání za běhu [SuspensionStarting –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)hostitel nesmí znovu naplánovat úlohu.</span><span class="sxs-lookup"><span data-stu-id="2a01c-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a01c-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a01c-126">Requirements</span></span>  
 <span data-ttu-id="2a01c-127">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a01c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a01c-128">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2a01c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a01c-129">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2a01c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a01c-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a01c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a01c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a01c-131">See also</span></span>

- [<span data-ttu-id="2a01c-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a01c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2a01c-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a01c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2a01c-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a01c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2a01c-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a01c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="2a01c-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a01c-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
