---
title: IHostGCManager::SuspensionStarting – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3e808c7ed03d7b4cc9dfe77389df6b2eff491f7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937711"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="37ec6-102">IHostGCManager::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="37ec6-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="37ec6-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) pozastavuje spouštění úkolů, aby bylo možné provést uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="37ec6-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ec6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37ec6-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="37ec6-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37ec6-105">Return Value</span></span>  
  
|<span data-ttu-id="37ec6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37ec6-106">HRESULT</span></span>|<span data-ttu-id="37ec6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="37ec6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37ec6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="37ec6-108">S_OK</span></span>|<span data-ttu-id="37ec6-109">`SuspensionStarting`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="37ec6-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="37ec6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37ec6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37ec6-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="37ec6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37ec6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37ec6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37ec6-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="37ec6-113">The call timed out.</span></span>|  
|<span data-ttu-id="37ec6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37ec6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37ec6-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="37ec6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37ec6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37ec6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37ec6-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="37ec6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37ec6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37ec6-118">E_FAIL</span></span>|<span data-ttu-id="37ec6-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="37ec6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37ec6-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="37ec6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37ec6-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37ec6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ec6-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37ec6-122">Remarks</span></span>  
 <span data-ttu-id="37ec6-123">CLR volá `SuspensionStarting` , aby informoval hostitele, ke kterému probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="37ec6-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37ec6-124">Tuto úlohu neplánujte znovu.</span><span class="sxs-lookup"><span data-stu-id="37ec6-124">Do not reschedule this task.</span></span> <span data-ttu-id="37ec6-125">Hostitel musí při volání [ThreadIsBlockingForSuspension –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) změnit plán úlohy.</span><span class="sxs-lookup"><span data-stu-id="37ec6-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ec6-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37ec6-126">Requirements</span></span>  
 <span data-ttu-id="37ec6-127">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ec6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ec6-128">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37ec6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37ec6-129">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37ec6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37ec6-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ec6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ec6-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37ec6-131">See also</span></span>

- [<span data-ttu-id="37ec6-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ec6-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="37ec6-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ec6-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="37ec6-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ec6-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="37ec6-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ec6-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="37ec6-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37ec6-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
