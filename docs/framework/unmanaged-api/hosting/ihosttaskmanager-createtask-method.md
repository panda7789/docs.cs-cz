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
ms.openlocfilehash: 7079a915c0402df62afa5648317619af82c943b0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841977"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="4289f-102">IHostTaskManager::CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="4289f-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="4289f-103">Požaduje, aby hostitel vytvořil novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="4289f-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4289f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4289f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4289f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4289f-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="4289f-106">pro Požadovaná velikost vyžádaného zásobníku (v bajtech), nebo 0 (nula) pro výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="4289f-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="4289f-107">pro Ukazatel na funkci, kterou má úkol provést.</span><span class="sxs-lookup"><span data-stu-id="4289f-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="4289f-108">pro Ukazatel na uživatelská data, která mají být předána funkci, nebo hodnotu null, pokud funkce nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="4289f-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="4289f-109">mimo Ukazatel na adresu instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) vytvořeného hostitelem nebo hodnotu null, pokud úlohu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4289f-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="4289f-110">Úloha zůstane v pozastaveném stavu, dokud není explicitně spuštěna voláním metody [IHostTask:: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="4289f-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4289f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4289f-111">Return Value</span></span>  
  
|<span data-ttu-id="4289f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4289f-112">HRESULT</span></span>|<span data-ttu-id="4289f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4289f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4289f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4289f-114">S_OK</span></span>|<span data-ttu-id="4289f-115">`CreateTask`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4289f-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="4289f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4289f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4289f-117">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4289f-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4289f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4289f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4289f-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4289f-119">The call timed out.</span></span>|  
|<span data-ttu-id="4289f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4289f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4289f-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4289f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4289f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4289f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4289f-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4289f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4289f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4289f-124">E_FAIL</span></span>|<span data-ttu-id="4289f-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4289f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4289f-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4289f-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4289f-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4289f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4289f-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4289f-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4289f-129">Pro vytvoření požadované úlohy není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="4289f-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4289f-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4289f-130">Remarks</span></span>  
 <span data-ttu-id="4289f-131">Modul CLR volá `CreateTask` požadavek na to, aby hostitel vytvořil nový úkol.</span><span class="sxs-lookup"><span data-stu-id="4289f-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="4289f-132">Hostitel vrátí ukazatel rozhraní na `IHostTask` instanci.</span><span class="sxs-lookup"><span data-stu-id="4289f-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="4289f-133">Vrácený úkol musí zůstat pozastaven, dokud není explicitně spuštěn voláním metody `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="4289f-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4289f-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4289f-134">Requirements</span></span>  
 <span data-ttu-id="4289f-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4289f-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4289f-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4289f-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4289f-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4289f-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4289f-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4289f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4289f-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4289f-139">See also</span></span>

- [<span data-ttu-id="4289f-140">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4289f-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4289f-141">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4289f-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4289f-142">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4289f-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4289f-143">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4289f-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
