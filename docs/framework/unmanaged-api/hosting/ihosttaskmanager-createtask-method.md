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
ms.openlocfilehash: 16916d62a528222db952a1d29dc7c69de2352191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133129"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="7cdd3-102">IHostTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="7cdd3-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="7cdd3-103">Požaduje, aby hostitel vytvořil novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdd3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cdd3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cdd3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cdd3-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="7cdd3-106">pro Požadovaná velikost vyžádaného zásobníku (v bajtech), nebo 0 (nula) pro výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="7cdd3-107">pro Ukazatel na funkci, kterou má úkol provést.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="7cdd3-108">pro Ukazatel na uživatelská data, která mají být předána funkci, nebo hodnotu null, pokud funkce nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="7cdd3-109">mimo Ukazatel na adresu instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) vytvořeného hostitelem nebo hodnotu null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="7cdd3-110">Úloha zůstane v pozastaveném stavu, dokud není explicitně spuštěna voláním metody [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="7cdd3-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cdd3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7cdd3-111">Return Value</span></span>  
  
|<span data-ttu-id="7cdd3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7cdd3-112">HRESULT</span></span>|<span data-ttu-id="7cdd3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7cdd3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cdd3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7cdd3-114">S_OK</span></span>|<span data-ttu-id="7cdd3-115">`CreateTask` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="7cdd3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7cdd3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7cdd3-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7cdd3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7cdd3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7cdd3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-119">The call timed out.</span></span>|  
|<span data-ttu-id="7cdd3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7cdd3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7cdd3-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7cdd3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7cdd3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7cdd3-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7cdd3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7cdd3-124">E_FAIL</span></span>|<span data-ttu-id="7cdd3-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7cdd3-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7cdd3-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7cdd3-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7cdd3-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7cdd3-129">Pro vytvoření požadované úlohy není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cdd3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cdd3-130">Remarks</span></span>  
 <span data-ttu-id="7cdd3-131">CLR volá `CreateTask` k vyžádání, že hostitel vytvoří novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="7cdd3-132">Hostitel vrátí ukazatel rozhraní na instanci `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="7cdd3-133">Vrácený úkol musí zůstat pozastaven, dokud není explicitně spuštěn voláním `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="7cdd3-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cdd3-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7cdd3-134">Requirements</span></span>  
 <span data-ttu-id="7cdd3-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cdd3-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cdd3-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7cdd3-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cdd3-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7cdd3-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cdd3-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cdd3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdd3-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cdd3-139">See also</span></span>

- [<span data-ttu-id="7cdd3-140">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cdd3-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="7cdd3-141">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cdd3-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="7cdd3-142">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cdd3-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="7cdd3-143">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cdd3-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
