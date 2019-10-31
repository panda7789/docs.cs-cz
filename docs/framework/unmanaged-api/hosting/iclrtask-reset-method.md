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
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124643"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="18882-102">ICLRTask::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="18882-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="18882-103">Informuje modul CLR (Common Language Runtime), který hostitel dokončil úlohu, a umožňuje, aby CLR znovu používá aktuální instanci [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) k tomu, aby reprezentovala jinou úlohu.</span><span class="sxs-lookup"><span data-stu-id="18882-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18882-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18882-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="18882-106">[in] `true`, pokud by měl modul runtime kromě informací o zabezpečení a národním prostředí, které souvisí s aktuální `ICLRTask` instancí, resetovat všechny statické hodnoty související s vlákny. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="18882-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="18882-107">Pokud je hodnota `true`, modul runtime obnoví data uložená pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="18882-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18882-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18882-108">Return Value</span></span>  
  
|<span data-ttu-id="18882-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18882-109">HRESULT</span></span>|<span data-ttu-id="18882-110">Popis</span><span class="sxs-lookup"><span data-stu-id="18882-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18882-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="18882-111">S_OK</span></span>|<span data-ttu-id="18882-112">`Reset` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="18882-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="18882-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18882-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18882-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18882-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="18882-115">Nepodařilo</span><span class="sxs-lookup"><span data-stu-id="18882-115">successfully</span></span>|  
|<span data-ttu-id="18882-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18882-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18882-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18882-117">The call timed out.</span></span>|  
|<span data-ttu-id="18882-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18882-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18882-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="18882-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18882-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18882-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18882-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="18882-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18882-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18882-122">E_FAIL</span></span>|<span data-ttu-id="18882-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="18882-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18882-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="18882-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18882-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18882-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18882-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18882-126">Remarks</span></span>  
 <span data-ttu-id="18882-127">Modul CLR může recyklovat dříve vytvořené `ICLRTask` instance, aby nedošlo k opakovanému vytváření nových instancí pokaždé, když potřebuje nový úkol.</span><span class="sxs-lookup"><span data-stu-id="18882-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="18882-128">Hostitel tuto funkci povolí voláním `ICLRTask::Reset` namísto [ICLRTask:: ExitTask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) , pokud dokončil úkol.</span><span class="sxs-lookup"><span data-stu-id="18882-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="18882-129">Následující seznam shrnuje normální životní cyklus instance `ICLRTask`:</span><span class="sxs-lookup"><span data-stu-id="18882-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="18882-130">Modul runtime vytvoří novou instanci `ICLRTask`.</span><span class="sxs-lookup"><span data-stu-id="18882-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="18882-131">Běhové volání [IHostTaskManager:: GetCurrentTask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) získá odkaz na aktuální úlohu hostitele.</span><span class="sxs-lookup"><span data-stu-id="18882-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="18882-132">Běhové volání [IHostTask:: SetCLRTask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) přiřadí novou instanci k úloze hostitele.</span><span class="sxs-lookup"><span data-stu-id="18882-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="18882-133">Úloha se spustí a dokončí.</span><span class="sxs-lookup"><span data-stu-id="18882-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="18882-134">Hostitel zničí úlohu voláním `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="18882-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="18882-135">`Reset` mění tento scénář dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="18882-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="18882-136">V kroku 5 výše Hostitel volá `Reset` pro resetování úlohy do čistého stavu a potom oddělí `ICLRTask` instanci od přidružené instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="18882-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="18882-137">V případě potřeby může hostitel také uložit instanci `IHostTask` do mezipaměti pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="18882-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="18882-138">V kroku 1 výše se modul runtime z mezipaměti vy`ICLRTask` žádá, místo aby se vytvořila nová instance.</span><span class="sxs-lookup"><span data-stu-id="18882-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="18882-139">Tento přístup funguje i v případě, že hostitel má také fond opakovaně použitelných pracovních úloh.</span><span class="sxs-lookup"><span data-stu-id="18882-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="18882-140">Když hostitel zničí jednu z jeho `IHostTask` instance, zničí odpovídající `ICLRTask` voláním `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="18882-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18882-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18882-141">Requirements</span></span>  
 <span data-ttu-id="18882-142">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18882-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18882-143">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18882-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18882-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18882-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18882-145">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18882-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18882-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18882-146">See also</span></span>

- [<span data-ttu-id="18882-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18882-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="18882-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18882-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="18882-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18882-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="18882-150">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18882-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
