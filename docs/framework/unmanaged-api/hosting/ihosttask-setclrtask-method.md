---
title: "IHostTask::SetCLRTask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="42432-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="42432-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="42432-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="42432-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42432-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42432-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42432-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42432-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="42432-106">[v] Ukazatele rozhraní na `ICLRTask` instance, která má být přidružen k aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="42432-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="42432-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="42432-107">Return Value</span></span>  
  
|<span data-ttu-id="42432-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="42432-108">HRESULT</span></span>|<span data-ttu-id="42432-109">Popis</span><span class="sxs-lookup"><span data-stu-id="42432-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="42432-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="42432-110">S_OK</span></span>|<span data-ttu-id="42432-111">`SetCLRTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="42432-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="42432-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="42432-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="42432-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="42432-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="42432-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="42432-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="42432-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="42432-115">The call timed out.</span></span>|  
|<span data-ttu-id="42432-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="42432-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="42432-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="42432-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="42432-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="42432-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="42432-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="42432-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="42432-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="42432-120">E_FAIL</span></span>|<span data-ttu-id="42432-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="42432-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="42432-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="42432-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="42432-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="42432-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42432-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42432-124">Remarks</span></span>  
 <span data-ttu-id="42432-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="42432-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42432-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42432-126">Requirements</span></span>  
 <span data-ttu-id="42432-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42432-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42432-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42432-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42432-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42432-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42432-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42432-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42432-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="42432-131">See Also</span></span>  
 [<span data-ttu-id="42432-132">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42432-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="42432-133">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42432-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="42432-134">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42432-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="42432-135">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42432-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
