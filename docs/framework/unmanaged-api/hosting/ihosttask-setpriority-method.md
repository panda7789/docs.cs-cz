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
ms.openlocfilehash: ac3a8479cdf05e55885bd55d4e4fb8e6e47686f9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842395"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="d446e-102">IHostTask::SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="d446e-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="d446e-103">Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální instancí [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d446e-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d446e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d446e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d446e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d446e-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="d446e-106">pro Celé číslo, které představuje požadovanou hodnotu priority vlákna pro úlohu reprezentovanou aktuální `IHostTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="d446e-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d446e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d446e-107">Return Value</span></span>  
  
|<span data-ttu-id="d446e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d446e-108">HRESULT</span></span>|<span data-ttu-id="d446e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d446e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d446e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d446e-110">S_OK</span></span>|<span data-ttu-id="d446e-111">`SetPriority`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d446e-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="d446e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d446e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d446e-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d446e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d446e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d446e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d446e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d446e-115">The call timed out.</span></span>|  
|<span data-ttu-id="d446e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d446e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d446e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d446e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d446e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d446e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d446e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d446e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d446e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d446e-120">E_FAIL</span></span>|<span data-ttu-id="d446e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d446e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d446e-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d446e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d446e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d446e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d446e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d446e-124">Remarks</span></span>  
 <span data-ttu-id="d446e-125">Vlákna jsou udělena doba zpracování pomocí systému kruhového dotazování, který je částečně založen na úrovni priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="d446e-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="d446e-126">`SetPriority`umožňuje modulu CLR nastavit pro aktuální úkol úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="d446e-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="d446e-127">`newPriority`Podporovány jsou následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d446e-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="d446e-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d446e-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="d446e-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d446e-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="d446e-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="d446e-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="d446e-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="d446e-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="d446e-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="d446e-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="d446e-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="d446e-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="d446e-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="d446e-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="d446e-135">CLR volá, `SetPriority` Když <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> je hodnota změněna pomocí uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="d446e-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="d446e-136">Hostitel může definovat vlastní algoritmy pro přiřazení priority vlákna a je zadarmo ignorovat tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="d446e-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d446e-137">`SetPriority`neoznamuje, zda byla změněna úroveň priority vlákna.</span><span class="sxs-lookup"><span data-stu-id="d446e-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="d446e-138">Voláním [IHostTask:: GetPriority](ihosttask-getpriority-method.md) určíte hodnotu úrovně priority vlákna úlohy.</span><span class="sxs-lookup"><span data-stu-id="d446e-138">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="d446e-139">Hodnoty úrovně priority vlákna jsou definovány `SetThreadPriority` funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="d446e-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="d446e-140">Další informace o prioritě vlákna najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="d446e-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d446e-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d446e-141">Requirements</span></span>  
 <span data-ttu-id="d446e-142">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d446e-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d446e-143">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d446e-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d446e-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d446e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d446e-145">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d446e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d446e-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="d446e-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="d446e-147">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d446e-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d446e-148">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d446e-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d446e-149">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d446e-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d446e-150">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="d446e-150">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="d446e-151">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d446e-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
