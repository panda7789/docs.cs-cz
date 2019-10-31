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
ms.openlocfilehash: bbb563a304e3ff7cdba3dfe7e394da9cf138ff10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121359"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="b38bb-102">IHostTask::SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="b38bb-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="b38bb-103">Přidruží instanci `ICLRTask` k aktuální instanci [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b38bb-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b38bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b38bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b38bb-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="b38bb-106">pro Ukazatel rozhraní na instanci `ICLRTask`, který má být přidružen k aktuální instanci `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="b38bb-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b38bb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b38bb-107">Return Value</span></span>  
  
|<span data-ttu-id="b38bb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b38bb-108">HRESULT</span></span>|<span data-ttu-id="b38bb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b38bb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b38bb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b38bb-110">S_OK</span></span>|<span data-ttu-id="b38bb-111">`SetCLRTask` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b38bb-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="b38bb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b38bb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b38bb-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b38bb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b38bb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b38bb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b38bb-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b38bb-115">The call timed out.</span></span>|  
|<span data-ttu-id="b38bb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b38bb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b38bb-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b38bb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b38bb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b38bb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b38bb-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b38bb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b38bb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b38bb-120">E_FAIL</span></span>|<span data-ttu-id="b38bb-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b38bb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b38bb-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b38bb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b38bb-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b38bb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b38bb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b38bb-124">Remarks</span></span>  
 <span data-ttu-id="b38bb-125">CLR volá `SetCLRTask` k přidružení instance `ICLRTask` s aktuální instancí `IHostTask`, která byla vytvořena voláním metody [IHostTaskManager:: CreateTask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="b38bb-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38bb-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b38bb-126">Requirements</span></span>  
 <span data-ttu-id="b38bb-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b38bb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38bb-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b38bb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b38bb-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b38bb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b38bb-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b38bb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b38bb-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b38bb-131">See also</span></span>

- [<span data-ttu-id="b38bb-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38bb-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="b38bb-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38bb-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="b38bb-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38bb-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="b38bb-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b38bb-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
