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
ms.openlocfilehash: 3039855a58e6db6a403ab33c226b4b8b390668f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758601"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="6e5ff-102">ICLRTask::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="6e5ff-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="6e5ff-103">Informuje o tom common language runtime (CLR), že byla dokončena úloha hostitele a umožňuje modulu CLR pro opětovné použití aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance k reprezentování jiného úkolu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e5ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e5ff-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="6e5ff-106">[in] `true`, pokud modul runtime by měl obnovit všechny statické hodnoty související vlákna plody kromě a informace o zabezpečení a národní prostředí aktuálního `ICLRTask` instance; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="6e5ff-107">Pokud je hodnota `true`, modul runtime obnoví data, která byla uložena pomocí <xref:System.Threading.Thread.AllocateDataSlot%2A> nebo <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e5ff-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6e5ff-108">Return Value</span></span>  
  
|<span data-ttu-id="6e5ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e5ff-109">HRESULT</span></span>|<span data-ttu-id="6e5ff-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6e5ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e5ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e5ff-111">S_OK</span></span>|<span data-ttu-id="6e5ff-112">`Reset` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="6e5ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e5ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e5ff-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nemůže spouštět spravovaný kód a zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="6e5ff-115">úspěšně</span><span class="sxs-lookup"><span data-stu-id="6e5ff-115">successfully</span></span>|  
|<span data-ttu-id="6e5ff-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e5ff-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e5ff-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-117">The call timed out.</span></span>|  
|<span data-ttu-id="6e5ff-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e5ff-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e5ff-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e5ff-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e5ff-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e5ff-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e5ff-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e5ff-122">E_FAIL</span></span>|<span data-ttu-id="6e5ff-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e5ff-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e5ff-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e5ff-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e5ff-126">Remarks</span></span>  
 <span data-ttu-id="6e5ff-127">Modul CLR recykluje dříve vytvořili `ICLRTask` instancí, aby režijní náklady na opakované vytváření nové instance pokaždé, když potřebuje novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="6e5ff-128">Hostitele povolí tuto funkci voláním `ICLRTask::Reset` místo [iclrtask::exittask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) po jeho dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="6e5ff-129">Následující seznam shrnuje běžné životní cyklus `ICLRTask` instance:</span><span class="sxs-lookup"><span data-stu-id="6e5ff-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="6e5ff-130">Vytvoří nový modul runtime `ICLRTask` instance.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="6e5ff-131">Modul runtime zavolá [ihosttaskmanager::getcurrenttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) získat odkaz na aktuální úlohu na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="6e5ff-132">Modul runtime zavolá [ihosttask::setclrtask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) přidružit nové instance hostitele úloh.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="6e5ff-133">Úloha spustí a dokončí.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="6e5ff-134">Hostitele odstraní úlohu voláním `ICLRTask::ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="6e5ff-135">`Reset` upravuje tento scénář dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="6e5ff-136">V kroku 5 výše volání hostitele `Reset` resetovat úlohy do čistého stavu a potom odpojí `ICLRTask` instanci z jeho přidruženého [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="6e5ff-137">V případě potřeby hostitele lze také ukládat do mezipaměti `IHostTask` instance pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="6e5ff-138">V kroku 1 výše, modul runtime si vyžádá recyklovat `ICLRTask` z mezipaměti místo vytvoření nové instance.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="6e5ff-139">Tento přístup funguje dobře, když se hostitel má také fondu úkolů opakovaně použitelného pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="6e5ff-140">Když hostitel odstraní jeden z jeho `IHostTask` instancí, zlikvidují odpovídající `ICLRTask` voláním `ExitTask`.</span><span class="sxs-lookup"><span data-stu-id="6e5ff-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e5ff-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e5ff-141">Requirements</span></span>  
 <span data-ttu-id="6e5ff-142">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e5ff-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5ff-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e5ff-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e5ff-144">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e5ff-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5ff-145">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5ff-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5ff-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e5ff-146">See also</span></span>

- [<span data-ttu-id="6e5ff-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5ff-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6e5ff-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5ff-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6e5ff-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5ff-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6e5ff-150">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5ff-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
