---
title: IHostTask::SetPriority – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5382341a8c0c6455438af9e8c476348ab2467a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189037"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="ccc3d-102">IHostTask::SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc3d-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="ccc3d-103">Požadavky, že hostitel upravit priorita vlákna na úrovni úkolů reprezentované aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccc3d-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccc3d-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="ccc3d-106">[in] Celé číslo představující hodnotu priority požadovaný vlákno pro úlohu reprezentované aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccc3d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ccc3d-107">Return Value</span></span>  
  
|<span data-ttu-id="ccc3d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ccc3d-108">HRESULT</span></span>|<span data-ttu-id="ccc3d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="ccc3d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ccc3d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ccc3d-110">S_OK</span></span>|<span data-ttu-id="ccc3d-111">`SetPriority` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="ccc3d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ccc3d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ccc3d-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ccc3d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ccc3d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ccc3d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-115">The call timed out.</span></span>|  
|<span data-ttu-id="ccc3d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ccc3d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ccc3d-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ccc3d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ccc3d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ccc3d-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ccc3d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ccc3d-120">E_FAIL</span></span>|<span data-ttu-id="ccc3d-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ccc3d-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ccc3d-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccc3d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccc3d-124">Remarks</span></span>  
 <span data-ttu-id="ccc3d-125">Vlákna jsou udělena zpracování čase s použitím systému kruhové dotazování, částečně založenou na úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="ccc3d-126">`SetPriority` Umožňuje nastavit prioritu tohoto vlákna pro aktuální úlohu na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="ccc3d-127">Následující `newPriority` hodnoty jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="ccc3d-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ccc3d-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="ccc3d-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ccc3d-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="ccc3d-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="ccc3d-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="ccc3d-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="ccc3d-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="ccc3d-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="ccc3d-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="ccc3d-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="ccc3d-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="ccc3d-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="ccc3d-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="ccc3d-135">Volání CLR `SetPriority` při hodnotu <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> upravit pomocí uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="ccc3d-136">Hostitele můžete definovat vlastní algoritmy pro přiřazení priority vlákna a je zdarma pro tuto žádost ignorovat.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ccc3d-137">`SetPriority` nevytváří sestavu, zda byla změněna úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="ccc3d-138">Volání [ihosttask::getpriority –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) k určení hodnoty úkolu úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="ccc3d-139">Hodnoty úroveň priority vlákna jsou definovány Win32 `SetThreadPriority` funkce.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="ccc3d-140">Další informace o priorita vlákna v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ccc3d-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc3d-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccc3d-141">Requirements</span></span>  
 <span data-ttu-id="ccc3d-142">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccc3d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc3d-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ccc3d-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ccc3d-144">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccc3d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccc3d-145">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc3d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc3d-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccc3d-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="ccc3d-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc3d-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ccc3d-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc3d-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ccc3d-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc3d-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ccc3d-150">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc3d-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="ccc3d-151">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc3d-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
