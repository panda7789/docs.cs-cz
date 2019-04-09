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
ms.openlocfilehash: b0220a0699e7325c6d81ba3ad4627176640937dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131960"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="51116-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="51116-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="51116-103">Přidruží `ICLRTask` instance s aktuálním [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="51116-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51116-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51116-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51116-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="51116-106">[in] Ukazatel rozhraní k `ICLRTask` instance má být spojen s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="51116-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51116-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51116-107">Return Value</span></span>  
  
|<span data-ttu-id="51116-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51116-108">HRESULT</span></span>|<span data-ttu-id="51116-109">Popis</span><span class="sxs-lookup"><span data-stu-id="51116-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51116-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51116-110">S_OK</span></span>|`SetCLRTask` <span data-ttu-id="51116-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="51116-111">returned successfully.</span></span>|  
|<span data-ttu-id="51116-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51116-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51116-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="51116-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51116-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51116-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51116-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="51116-115">The call timed out.</span></span>|  
|<span data-ttu-id="51116-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51116-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51116-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="51116-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51116-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51116-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51116-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="51116-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51116-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51116-120">E_FAIL</span></span>|<span data-ttu-id="51116-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="51116-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51116-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="51116-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51116-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="51116-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51116-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51116-124">Remarks</span></span>  
 <span data-ttu-id="51116-125">Volání CLR `SetCLRTask` pro přidružení `ICLRTask` instance s aktuálním `IHostTask` instance, který byl vytvořen voláním [ihosttaskmanager::createtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="51116-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51116-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51116-126">Requirements</span></span>  
 <span data-ttu-id="51116-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51116-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51116-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51116-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51116-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51116-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="51116-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="51116-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="51116-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51116-131">See also</span></span>

- [<span data-ttu-id="51116-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51116-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="51116-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51116-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="51116-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51116-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="51116-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51116-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
