---
title: ICLRTask::Reset – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29267d032f5e38e352592edc50dbded68aaa9f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435939"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="90a64-102">ICLRTask::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="90a64-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="90a64-103">Modul CLR (CLR) informuje, že byla dokončena úloha hostitele a umožňuje CLR znovu použít aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představují jiná úloha.</span><span class="sxs-lookup"><span data-stu-id="90a64-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90a64-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90a64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90a64-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="90a64-106">[v] `true`, pokud by se modul runtime obnovit všechny statické hodnoty související s vlákno plody kromě a informace o zabezpečení a národního prostředí aktuálního `ICLRTask` instanci, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="90a64-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="90a64-107">Pokud je hodnota `true`, modul runtime obnoví data, která byla uložená pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="90a64-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90a64-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90a64-108">Return Value</span></span>  
  
|<span data-ttu-id="90a64-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90a64-109">HRESULT</span></span>|<span data-ttu-id="90a64-110">Popis</span><span class="sxs-lookup"><span data-stu-id="90a64-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90a64-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="90a64-111">S_OK</span></span>|<span data-ttu-id="90a64-112">`Reset` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="90a64-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="90a64-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="90a64-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="90a64-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže spustit spravovaného kódu nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="90a64-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="90a64-115">úspěšně</span><span class="sxs-lookup"><span data-stu-id="90a64-115">successfully</span></span>|  
|<span data-ttu-id="90a64-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="90a64-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="90a64-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="90a64-117">The call timed out.</span></span>|  
|<span data-ttu-id="90a64-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="90a64-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="90a64-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="90a64-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="90a64-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="90a64-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="90a64-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="90a64-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="90a64-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="90a64-122">E_FAIL</span></span>|<span data-ttu-id="90a64-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="90a64-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="90a64-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="90a64-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="90a64-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="90a64-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90a64-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90a64-126">Remarks</span></span>  
 <span data-ttu-id="90a64-127">Modul CLR provést recyklaci vytvořili `ICLRTask` instancí, aby se zabránilo režii opakovaně vytváření nových instancí pokaždé, když potřebuje novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="90a64-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="90a64-128">Hostitele povolí tuto funkci voláním `ICLRTask::Reset` místo [iclrtask::exittask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po jeho dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="90a64-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="90a64-129">Následující seznam shrnuje normální životní cyklus `ICLRTask` instance:</span><span class="sxs-lookup"><span data-stu-id="90a64-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="90a64-130">Vytvoří nový modul runtime `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="90a64-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="90a64-131">Volání modulu runtime [ihosttaskmanager::getcurrenttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) získat odkaz na aktuální úlohy hostitele.</span><span class="sxs-lookup"><span data-stu-id="90a64-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="90a64-132">Volání modulu runtime [ihosttask::setclrtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) přidružit nové instance hostitele úloh.</span><span class="sxs-lookup"><span data-stu-id="90a64-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="90a64-133">Úloha se spustí a dokončení.</span><span class="sxs-lookup"><span data-stu-id="90a64-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="90a64-134">Hostitel zničí úlohy voláním `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="90a64-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="90a64-135">`Reset` mění tento scénář dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="90a64-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="90a64-136">V kroku 5 výše, volání hostitele `Reset` resetovat úlohu do čistého stavu a potom odpojí `ICLRTask` instance z jeho přidružených [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="90a64-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="90a64-137">V případě potřeby můžete také mezipaměti hostitele `IHostTask` instance pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="90a64-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="90a64-138">V kroku 1 výše, modul runtime vrátí recykluje `ICLRTask` z mezipaměti místo vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="90a64-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="90a64-139">Tento postup funguje dobře, pokud hostitel má také fond znovu použitelné pracovní úkoly.</span><span class="sxs-lookup"><span data-stu-id="90a64-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="90a64-140">Když hostitel zničí jeden z jeho `IHostTask` instancí ho zničí odpovídající `ICLRTask` voláním `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="90a64-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90a64-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90a64-141">Requirements</span></span>  
 <span data-ttu-id="90a64-142">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90a64-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a64-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90a64-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90a64-144">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90a64-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90a64-145">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90a64-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a64-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="90a64-146">See Also</span></span>  
 [<span data-ttu-id="90a64-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90a64-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="90a64-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90a64-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="90a64-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90a64-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="90a64-150">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90a64-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
