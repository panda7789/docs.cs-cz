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
ms.openlocfilehash: 13e4119da7af4c54387c24ee576ff9577da56ca9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438038"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="8f71e-102">ICLRTask::SwitchIn – metoda</span><span class="sxs-lookup"><span data-stu-id="8f71e-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="8f71e-103">Upozorní common language runtime (CLR), úlohy, aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) představuje instanci je nyní v spustitelného stavu.</span><span class="sxs-lookup"><span data-stu-id="8f71e-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f71e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f71e-104">Syntax</span></span>  
  
```  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f71e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f71e-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="8f71e-106">[v] Popisovač pro fyzické vláken, na kterém úlohu reprezentována aktuální `ICLRTask` spouští instance.</span><span class="sxs-lookup"><span data-stu-id="8f71e-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f71e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8f71e-107">Return Value</span></span>  
  
|<span data-ttu-id="8f71e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f71e-108">HRESULT</span></span>|<span data-ttu-id="8f71e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8f71e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f71e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f71e-110">S_OK</span></span>|<span data-ttu-id="8f71e-111">`SwitchIn` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8f71e-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="8f71e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f71e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f71e-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8f71e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f71e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f71e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f71e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8f71e-115">The call timed out.</span></span>|  
|<span data-ttu-id="8f71e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f71e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f71e-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="8f71e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f71e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f71e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f71e-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="8f71e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f71e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f71e-120">E_FAIL</span></span>|<span data-ttu-id="8f71e-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="8f71e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f71e-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8f71e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f71e-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f71e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f71e-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="8f71e-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="8f71e-125">`SwitchIn` byla volána bez starší volání [switchout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f71e-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f71e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f71e-126">Remarks</span></span>  
 <span data-ttu-id="8f71e-127">`threadHandle` Parametr představuje popisovač vláknu operačního systému, na kterém úlohu reprezentována aktuální `ICLRTask` bylo naplánováno instance.</span><span class="sxs-lookup"><span data-stu-id="8f71e-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="8f71e-128">Pokud v tomto podprocesu došlo k zosobnění, musí volat [ihostsecuritymanager::RevertToSelf –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) před přepnutím v úloze.</span><span class="sxs-lookup"><span data-stu-id="8f71e-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f71e-129">Volání `SwitchIn` bez starší volání `SwitchOut` s hodnotou HRESULT HOST_E_INVALIDOPERATION se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="8f71e-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f71e-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f71e-130">Requirements</span></span>  
 <span data-ttu-id="8f71e-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f71e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f71e-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f71e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f71e-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f71e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f71e-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f71e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f71e-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f71e-135">See Also</span></span>  
 [<span data-ttu-id="8f71e-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f71e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8f71e-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f71e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8f71e-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f71e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8f71e-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f71e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
