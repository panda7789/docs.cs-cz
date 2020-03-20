---
title: IHostTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177989"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="cc7a2-102">IHostTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7a2-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="cc7a2-103">Požaduje, aby hostitel vytvořil nový úkol.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7a2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc7a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc7a2-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="cc7a2-106">[v] Požadovaná velikost v bajtech požadovaného zásobníku nebo 0 (nula) pro výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="cc7a2-107">[v] Ukazatel na funkci, kterou má úloha provést.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="cc7a2-108">[v] Ukazatel na uživatelská data, která mají být předána funkci, nebo null, pokud funkce nepřebírá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="cc7a2-109">[out] Ukazatel na adresu instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) vytvořené hostitelem nebo null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="cc7a2-110">Úloha zůstane v pozastaveném stavu, dokud není explicitně spuštěna voláním [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="cc7a2-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc7a2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cc7a2-111">Return Value</span></span>  
  
|<span data-ttu-id="cc7a2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc7a2-112">HRESULT</span></span>|<span data-ttu-id="cc7a2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="cc7a2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc7a2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc7a2-114">S_OK</span></span>|<span data-ttu-id="cc7a2-115">`CreateTask`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="cc7a2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc7a2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc7a2-117">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc7a2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc7a2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc7a2-119">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-119">The call timed out.</span></span>|  
|<span data-ttu-id="cc7a2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc7a2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc7a2-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc7a2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc7a2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc7a2-123">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc7a2-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="cc7a2-124">E_FAIL</span></span>|<span data-ttu-id="cc7a2-125">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc7a2-126">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc7a2-127">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cc7a2-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cc7a2-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cc7a2-129">K vytvoření požadované úlohy nebylo k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc7a2-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc7a2-130">Remarks</span></span>  
 <span data-ttu-id="cc7a2-131">Volání CLR `CreateTask` požadovat, aby hostitel vytvořit nový úkol.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="cc7a2-132">Hostitel vrátí ukazatel rozhraní `IHostTask` k instanci.</span><span class="sxs-lookup"><span data-stu-id="cc7a2-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="cc7a2-133">Vrácená úloha musí zůstat pozastavena, dokud `IHostTask::Start`není explicitně spuštěna voláním .</span><span class="sxs-lookup"><span data-stu-id="cc7a2-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7a2-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc7a2-134">Requirements</span></span>  
 <span data-ttu-id="cc7a2-135">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7a2-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7a2-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc7a2-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc7a2-137">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc7a2-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc7a2-138">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7a2-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7a2-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc7a2-139">See also</span></span>

- [<span data-ttu-id="cc7a2-140">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7a2-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="cc7a2-141">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7a2-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="cc7a2-142">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7a2-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="cc7a2-143">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7a2-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
