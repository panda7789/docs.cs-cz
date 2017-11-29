---
title: "ICLRTask::SwitchIn – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.SwitchIn
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01e91c4febfebf8ec8ffd4c0ffbf8e33a4ff0edd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="92049-102">ICLRTask::SwitchIn – metoda</span><span class="sxs-lookup"><span data-stu-id="92049-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="92049-103">Upozorní common language runtime (CLR), úlohy, aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) představuje instanci je nyní v spustitelného stavu.</span><span class="sxs-lookup"><span data-stu-id="92049-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92049-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92049-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92049-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92049-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="92049-106">[v] Popisovač pro fyzické vláken, na kterém úlohu reprezentována aktuální `ICLRTask` spouští instance.</span><span class="sxs-lookup"><span data-stu-id="92049-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92049-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92049-107">Return Value</span></span>  
  
|<span data-ttu-id="92049-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92049-108">HRESULT</span></span>|<span data-ttu-id="92049-109">Popis</span><span class="sxs-lookup"><span data-stu-id="92049-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92049-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="92049-110">S_OK</span></span>|<span data-ttu-id="92049-111">`SwitchIn`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="92049-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="92049-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92049-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92049-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="92049-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92049-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92049-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92049-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="92049-115">The call timed out.</span></span>|  
|<span data-ttu-id="92049-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92049-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92049-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="92049-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92049-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92049-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92049-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="92049-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92049-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92049-120">E_FAIL</span></span>|<span data-ttu-id="92049-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="92049-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92049-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="92049-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92049-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92049-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92049-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="92049-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="92049-125">`SwitchIn`byla volána bez starší volání [switchout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="92049-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92049-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92049-126">Remarks</span></span>  
 <span data-ttu-id="92049-127">`threadHandle` Parametr představuje popisovač vláknu operačního systému, na kterém úlohu reprezentována aktuální `ICLRTask` bylo naplánováno instance.</span><span class="sxs-lookup"><span data-stu-id="92049-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="92049-128">Pokud v tomto podprocesu došlo k zosobnění, musí volat [ihostsecuritymanager::RevertToSelf –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) před přepnutím v úloze.</span><span class="sxs-lookup"><span data-stu-id="92049-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92049-129">Volání `SwitchIn` bez starší volání `SwitchOut` s hodnotou HRESULT HOST_E_INVALIDOPERATION se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="92049-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92049-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92049-130">Requirements</span></span>  
 <span data-ttu-id="92049-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92049-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92049-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92049-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92049-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92049-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92049-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92049-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92049-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="92049-135">See Also</span></span>  
 [<span data-ttu-id="92049-136">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92049-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="92049-137">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92049-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="92049-138">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92049-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="92049-139">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92049-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
