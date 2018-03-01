---
title: "IHostTask::SetCLRTask – metoda"
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
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 680ad2c13d8d6fc24134c9399cffb236bd637057
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="0c46d-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="0c46d-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="0c46d-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="0c46d-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c46d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c46d-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c46d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c46d-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="0c46d-106">[v] Ukazatele rozhraní na `ICLRTask` instance, která má být přidružen k aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="0c46d-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c46d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c46d-107">Return Value</span></span>  
  
|<span data-ttu-id="0c46d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c46d-108">HRESULT</span></span>|<span data-ttu-id="0c46d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0c46d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c46d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c46d-110">S_OK</span></span>|<span data-ttu-id="0c46d-111">`SetCLRTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0c46d-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="0c46d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c46d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c46d-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0c46d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0c46d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0c46d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0c46d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0c46d-115">The call timed out.</span></span>|  
|<span data-ttu-id="0c46d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0c46d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0c46d-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0c46d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0c46d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0c46d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0c46d-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0c46d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0c46d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c46d-120">E_FAIL</span></span>|<span data-ttu-id="0c46d-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0c46d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0c46d-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0c46d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0c46d-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0c46d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c46d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c46d-124">Remarks</span></span>  
 <span data-ttu-id="0c46d-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c46d-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c46d-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c46d-126">Requirements</span></span>  
 <span data-ttu-id="0c46d-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c46d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c46d-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c46d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c46d-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c46d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c46d-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c46d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c46d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c46d-131">See Also</span></span>  
 [<span data-ttu-id="0c46d-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c46d-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0c46d-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c46d-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0c46d-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c46d-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0c46d-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c46d-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
