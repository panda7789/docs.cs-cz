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
ms.openlocfilehash: ccc08ae210dd02bc71a1d83bc81525a7308c20e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770381"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="aff49-102">ICLRTask::SwitchIn – metoda</span><span class="sxs-lookup"><span data-stu-id="aff49-102">ICLRTask::SwitchIn Method</span></span>
<span data-ttu-id="aff49-103">Upozorní common language runtime (CLR), která úkol, který aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) představuje instanci je teď v provozuschopného stavu.</span><span class="sxs-lookup"><span data-stu-id="aff49-103">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aff49-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aff49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aff49-105">Parameters</span></span>  
 `threadHandle`  
 <span data-ttu-id="aff49-106">[in] Popisovač na fyzické vlákno, na kterém úloha reprezentována aktuální `ICLRTask` provádění instance.</span><span class="sxs-lookup"><span data-stu-id="aff49-106">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aff49-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aff49-107">Return Value</span></span>  
  
|<span data-ttu-id="aff49-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aff49-108">HRESULT</span></span>|<span data-ttu-id="aff49-109">Popis</span><span class="sxs-lookup"><span data-stu-id="aff49-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aff49-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aff49-110">S_OK</span></span>|<span data-ttu-id="aff49-111">`SwitchIn` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="aff49-111">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="aff49-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aff49-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aff49-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aff49-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aff49-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aff49-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aff49-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="aff49-115">The call timed out.</span></span>|  
|<span data-ttu-id="aff49-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aff49-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aff49-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="aff49-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aff49-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aff49-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aff49-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="aff49-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aff49-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aff49-120">E_FAIL</span></span>|<span data-ttu-id="aff49-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="aff49-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aff49-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="aff49-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aff49-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aff49-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aff49-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="aff49-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="aff49-125">`SwitchIn` byla volána bez dřívějším volání [switchout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span><span class="sxs-lookup"><span data-stu-id="aff49-125">`SwitchIn` was called without an earlier call to [SwitchOut Method](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aff49-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aff49-126">Remarks</span></span>  
 <span data-ttu-id="aff49-127">`threadHandle` Parametr představuje popisovač vlákna operačního systému, na kterém úloha reprezentována aktuální `ICLRTask` instance je naplánovaná.</span><span class="sxs-lookup"><span data-stu-id="aff49-127">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="aff49-128">Pokud v tomto vlákně došlo k zosobnění, musíte zavolat [ihostsecuritymanager::RevertToSelf –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) před přepnutím v úloze.</span><span class="sxs-lookup"><span data-stu-id="aff49-128">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff49-129">Volání `SwitchIn` bez dřívějším volání `SwitchOut` s hodnotou HRESULT HOST_E_INVALIDOPERATION se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="aff49-129">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aff49-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aff49-130">Requirements</span></span>  
 <span data-ttu-id="aff49-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aff49-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aff49-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aff49-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aff49-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aff49-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aff49-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aff49-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff49-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aff49-135">See also</span></span>

- [<span data-ttu-id="aff49-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aff49-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aff49-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aff49-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aff49-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aff49-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aff49-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aff49-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
