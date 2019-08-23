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
ms.openlocfilehash: 533e3d715b46b4ef6d473795a010fa3ad297ded2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913755"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="da237-102">IHostTask::SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="da237-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="da237-103">Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální instancí [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="da237-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da237-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da237-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="da237-106">pro Celé číslo, které představuje požadovanou hodnotu priority vlákna pro úlohu reprezentovanou aktuální `IHostTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="da237-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da237-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da237-107">Return Value</span></span>  
  
|<span data-ttu-id="da237-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da237-108">HRESULT</span></span>|<span data-ttu-id="da237-109">Popis</span><span class="sxs-lookup"><span data-stu-id="da237-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da237-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="da237-110">S_OK</span></span>|<span data-ttu-id="da237-111">`SetPriority`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="da237-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="da237-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da237-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da237-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="da237-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da237-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da237-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da237-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="da237-115">The call timed out.</span></span>|  
|<span data-ttu-id="da237-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da237-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da237-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="da237-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da237-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da237-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da237-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="da237-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da237-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da237-120">E_FAIL</span></span>|<span data-ttu-id="da237-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="da237-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da237-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="da237-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da237-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da237-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da237-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da237-124">Remarks</span></span>  
 <span data-ttu-id="da237-125">Vlákna jsou udělena doba zpracování pomocí systému kruhového dotazování, který je částečně založen na úrovni priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="da237-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="da237-126">`SetPriority`umožňuje modulu CLR nastavit pro aktuální úkol úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="da237-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="da237-127">Podporovány jsou `newPriority` následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da237-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="da237-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="da237-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="da237-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="da237-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="da237-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="da237-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="da237-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="da237-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="da237-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="da237-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="da237-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="da237-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="da237-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="da237-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="da237-135">CLR volá `SetPriority` , když <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> je hodnota změněna pomocí uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="da237-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="da237-136">Hostitel může definovat vlastní algoritmy pro přiřazení priority vlákna a je zadarmo ignorovat tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="da237-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da237-137">`SetPriority`neoznamuje, zda byla změněna úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="da237-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="da237-138">Voláním [IHostTask:: GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) určíte hodnotu úrovně priority vlákna úlohy.</span><span class="sxs-lookup"><span data-stu-id="da237-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="da237-139">Hodnoty úrovně priority vlákna jsou definovány funkcí Win32 `SetThreadPriority` .</span><span class="sxs-lookup"><span data-stu-id="da237-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="da237-140">Další informace o prioritě vlákna najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="da237-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da237-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da237-141">Requirements</span></span>  
 <span data-ttu-id="da237-142">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da237-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da237-143">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="da237-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da237-144">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da237-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da237-145">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da237-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da237-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da237-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="da237-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da237-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="da237-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da237-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="da237-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da237-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="da237-150">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="da237-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="da237-151">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da237-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
