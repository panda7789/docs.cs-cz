---
title: "IHostTaskManager::GetCurrentTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92b4ed0cd33d2e9d3399e409d2dba4eeb14a2f5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="fc700-102">IHostTaskManager::GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="fc700-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="fc700-103">Získá ukazatele rozhraní pro úlohu, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého přišla tato žádost.</span><span class="sxs-lookup"><span data-stu-id="fc700-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc700-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc700-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc700-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc700-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="fc700-106">[out] Ukazatel na adresu [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instanci, která představuje aktuálně spuštěné úlohy nebo null, pokud je aktuálně spuštěné žádné úlohy.</span><span class="sxs-lookup"><span data-stu-id="fc700-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc700-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fc700-107">Return Value</span></span>  
  
|<span data-ttu-id="fc700-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc700-108">HRESULT</span></span>|<span data-ttu-id="fc700-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fc700-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc700-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc700-110">S_OK</span></span>|<span data-ttu-id="fc700-111">`GetCurrentTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fc700-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="fc700-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc700-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc700-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fc700-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc700-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc700-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc700-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fc700-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc700-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc700-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc700-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="fc700-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc700-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc700-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc700-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="fc700-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc700-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc700-120">E_FAIL</span></span>|<span data-ttu-id="fc700-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="fc700-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc700-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fc700-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc700-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc700-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc700-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fc700-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fc700-125">`GetCurrentTask`byla volána ve vlákně operačního systému mimo ovládací prvek hostitele.</span><span class="sxs-lookup"><span data-stu-id="fc700-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc700-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc700-126">Remarks</span></span>  
 <span data-ttu-id="fc700-127">Hostitele lze také nastavit `pTask` parametr na hodnotu null pro úlohu, která nezahájila zabránit v přechodu do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fc700-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc700-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc700-128">Requirements</span></span>  
 <span data-ttu-id="fc700-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc700-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc700-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc700-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc700-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc700-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc700-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc700-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc700-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc700-133">See Also</span></span>  
 [<span data-ttu-id="fc700-134">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc700-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fc700-135">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc700-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fc700-136">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc700-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fc700-137">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc700-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
