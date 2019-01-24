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
ms.openlocfilehash: bce823bd6a9ad26a705649a666aeb97dcfa0cdbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636544"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="57a54-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="57a54-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="57a54-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="57a54-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57a54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57a54-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57a54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57a54-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="57a54-106">[in] Ukazatel rozhraní k `ICLRTask` instance má být spojen s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="57a54-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57a54-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="57a54-107">Return Value</span></span>  
  
|<span data-ttu-id="57a54-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57a54-108">HRESULT</span></span>|<span data-ttu-id="57a54-109">Popis</span><span class="sxs-lookup"><span data-stu-id="57a54-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57a54-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57a54-110">S_OK</span></span>|<span data-ttu-id="57a54-111">`SetCLRTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="57a54-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="57a54-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57a54-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57a54-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="57a54-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57a54-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57a54-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57a54-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="57a54-115">The call timed out.</span></span>|  
|<span data-ttu-id="57a54-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57a54-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57a54-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="57a54-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57a54-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57a54-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57a54-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="57a54-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57a54-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57a54-120">E_FAIL</span></span>|<span data-ttu-id="57a54-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="57a54-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57a54-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="57a54-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57a54-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57a54-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a54-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57a54-124">Remarks</span></span>  
 <span data-ttu-id="57a54-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="57a54-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57a54-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57a54-126">Requirements</span></span>  
 <span data-ttu-id="57a54-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a54-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57a54-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57a54-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57a54-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57a54-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57a54-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57a54-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a54-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57a54-131">See also</span></span>
- [<span data-ttu-id="57a54-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57a54-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="57a54-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57a54-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="57a54-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57a54-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="57a54-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57a54-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
