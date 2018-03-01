---
title: "IHostTaskManager::GetCurrentTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3ba8cbaac28df49a2df70492c1a292ee8cd287e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="90fbf-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="90fbf-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="90fbf-103">Získá ukazatele rozhraní pro úlohu, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého přišla tato žádost.</span><span class="sxs-lookup"><span data-stu-id="90fbf-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fbf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90fbf-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90fbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90fbf-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="90fbf-106">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje aktuálně spuštěné úlohy nebo null, pokud je aktuálně spuštěné žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="90fbf-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90fbf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90fbf-107">Return Value</span></span>  
  
|<span data-ttu-id="90fbf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90fbf-108">HRESULT</span></span>|<span data-ttu-id="90fbf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="90fbf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90fbf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="90fbf-110">S_OK</span></span>|<span data-ttu-id="90fbf-111">`GetCurrentTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="90fbf-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="90fbf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90fbf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90fbf-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="90fbf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="90fbf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90fbf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90fbf-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="90fbf-115">The call timed out.</span></span>|  
|<span data-ttu-id="90fbf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90fbf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90fbf-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="90fbf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90fbf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90fbf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90fbf-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="90fbf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90fbf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90fbf-120">E_FAIL</span></span>|<span data-ttu-id="90fbf-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="90fbf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90fbf-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="90fbf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90fbf-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="90fbf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="90fbf-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="90fbf-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="90fbf-125">`GetCurrentTask`byla volána ve vlákně operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="90fbf-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90fbf-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90fbf-126">Remarks</span></span>  
 <span data-ttu-id="90fbf-127">Hostitele lze také nastavit `pTask` parametr na hodnotu null pro úlohu, která nezahájila zabránit v přechodu do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="90fbf-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90fbf-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90fbf-128">Requirements</span></span>  
 <span data-ttu-id="90fbf-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90fbf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90fbf-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90fbf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90fbf-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90fbf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90fbf-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90fbf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fbf-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="90fbf-133">See Also</span></span>  
 [<span data-ttu-id="90fbf-134">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90fbf-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="90fbf-135">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90fbf-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="90fbf-136">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90fbf-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="90fbf-137">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90fbf-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
