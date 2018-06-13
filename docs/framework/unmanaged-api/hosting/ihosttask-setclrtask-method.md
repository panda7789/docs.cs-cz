---
title: IHostTask::SetCLRTask – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2149293989136e0b006f044c925353efbfd94031
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442797"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="eadd2-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="eadd2-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="eadd2-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="eadd2-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eadd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eadd2-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eadd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eadd2-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="eadd2-106">[v] Ukazatele rozhraní na `ICLRTask` instance, která má být přidružen k aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="eadd2-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eadd2-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eadd2-107">Return Value</span></span>  
  
|<span data-ttu-id="eadd2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eadd2-108">HRESULT</span></span>|<span data-ttu-id="eadd2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="eadd2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eadd2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eadd2-110">S_OK</span></span>|<span data-ttu-id="eadd2-111">`SetCLRTask` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="eadd2-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="eadd2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eadd2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eadd2-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="eadd2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eadd2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eadd2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eadd2-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="eadd2-115">The call timed out.</span></span>|  
|<span data-ttu-id="eadd2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eadd2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eadd2-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="eadd2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eadd2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eadd2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eadd2-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="eadd2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eadd2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eadd2-120">E_FAIL</span></span>|<span data-ttu-id="eadd2-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="eadd2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eadd2-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="eadd2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eadd2-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eadd2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eadd2-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eadd2-124">Remarks</span></span>  
 <span data-ttu-id="eadd2-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="eadd2-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eadd2-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eadd2-126">Requirements</span></span>  
 <span data-ttu-id="eadd2-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eadd2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eadd2-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eadd2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eadd2-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eadd2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eadd2-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eadd2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eadd2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="eadd2-131">See Also</span></span>  
 [<span data-ttu-id="eadd2-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eadd2-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="eadd2-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eadd2-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="eadd2-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eadd2-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="eadd2-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eadd2-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
