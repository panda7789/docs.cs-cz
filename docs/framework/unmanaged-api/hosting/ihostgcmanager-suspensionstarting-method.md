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
ms.openlocfilehash: bf1b830f55110c00356527bc9caa41dfd94ae377
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130458"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="c0aa6-102">IHostGCManager::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="c0aa6-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="c0aa6-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) pozastavuje spouštění úkolů, aby bylo možné provést uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0aa6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0aa6-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c0aa6-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0aa6-105">Return Value</span></span>  
  
|<span data-ttu-id="c0aa6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0aa6-106">HRESULT</span></span>|<span data-ttu-id="c0aa6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c0aa6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0aa6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0aa6-108">S_OK</span></span>|<span data-ttu-id="c0aa6-109">`SuspensionStarting` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="c0aa6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c0aa6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c0aa6-111">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c0aa6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c0aa6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c0aa6-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-113">The call timed out.</span></span>|  
|<span data-ttu-id="c0aa6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c0aa6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c0aa6-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c0aa6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c0aa6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c0aa6-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c0aa6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c0aa6-118">E_FAIL</span></span>|<span data-ttu-id="c0aa6-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c0aa6-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c0aa6-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0aa6-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0aa6-122">Remarks</span></span>  
 <span data-ttu-id="c0aa6-123">CLR volá `SuspensionStarting` k informování hostitele, ke kterému dochází uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c0aa6-124">Tuto úlohu neplánujte znovu.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-124">Do not reschedule this task.</span></span> <span data-ttu-id="c0aa6-125">Hostitel musí při volání [ThreadIsBlockingForSuspension –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) změnit plán úlohy.</span><span class="sxs-lookup"><span data-stu-id="c0aa6-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0aa6-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0aa6-126">Requirements</span></span>  
 <span data-ttu-id="c0aa6-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0aa6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0aa6-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0aa6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0aa6-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0aa6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0aa6-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0aa6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0aa6-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0aa6-131">See also</span></span>

- [<span data-ttu-id="c0aa6-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0aa6-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c0aa6-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0aa6-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c0aa6-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0aa6-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c0aa6-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0aa6-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="c0aa6-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0aa6-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
