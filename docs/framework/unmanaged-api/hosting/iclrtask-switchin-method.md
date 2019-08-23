---
title: ICLRTask::SwitchIn – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f408dd5e4d383040d9e3c03cd5bba8ebd320610f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938370"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="fb800-102">ICLRTask::SwitchIn – metoda</span><span class="sxs-lookup"><span data-stu-id="fb800-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="fb800-103">Upozorní modul CLR (Common Language Runtime) na to, že úloha, kterou aktuální instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) představuje, je teď v provozuschopném stavu.</span><span class="sxs-lookup"><span data-stu-id="fb800-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb800-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb800-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb800-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="fb800-106">pro Popisovač fyzického vlákna, na kterém je spuštěna úloha reprezentovaná aktuální `ICLRTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="fb800-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb800-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fb800-107">Return Value</span></span>  
  
|<span data-ttu-id="fb800-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb800-108">HRESULT</span></span>|<span data-ttu-id="fb800-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fb800-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb800-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb800-110">S_OK</span></span>|<span data-ttu-id="fb800-111">`SwitchIn`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fb800-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="fb800-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb800-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb800-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fb800-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb800-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb800-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb800-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fb800-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb800-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb800-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb800-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="fb800-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb800-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb800-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb800-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="fb800-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb800-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb800-120">E_FAIL</span></span>|<span data-ttu-id="fb800-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="fb800-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb800-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="fb800-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb800-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fb800-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb800-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fb800-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fb800-125">`SwitchIn`byla volána bez předchozího volání [metody Switch](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="fb800-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb800-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb800-126">Remarks</span></span>  
 <span data-ttu-id="fb800-127">Parametr představuje popisovač vlákna operačního systému, na kterém byla naplánována úloha reprezentovaná aktuální `ICLRTask` instancí. `threadHandle`</span><span class="sxs-lookup"><span data-stu-id="fb800-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="fb800-128">Pokud došlo k zosobnění v tomto vláknu, musíte před přepnutím do úlohy zavolat [IHostSecurityManager:: RevertToSelf –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fb800-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb800-129">Volání `SwitchIn` bez předchozího `SwitchOut` volání se nezdařila s hodnotou HRESULT HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="fb800-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb800-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb800-130">Requirements</span></span>  
 <span data-ttu-id="fb800-131">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb800-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb800-132">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb800-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb800-133">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fb800-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb800-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb800-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb800-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb800-135">See also</span></span>

- [<span data-ttu-id="fb800-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb800-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fb800-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb800-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fb800-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb800-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fb800-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb800-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
