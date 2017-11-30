---
title: "IHostTask::SetPriority – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34dabcb35f46d4a2b0536e00fa1fd69637b14cb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="7a636-102">IHostTask::SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="7a636-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="7a636-103">Požadavky, že hostitel upravit prioritu podprocesu úrovně pro úlohu reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="7a636-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a636-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a636-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a636-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a636-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="7a636-106">[v] Celé číslo, které představuje hodnota priority požadovaný přístup z více vláken pro úlohu reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="7a636-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a636-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7a636-107">Return Value</span></span>  
  
|<span data-ttu-id="7a636-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a636-108">HRESULT</span></span>|<span data-ttu-id="7a636-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7a636-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a636-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a636-110">S_OK</span></span>|<span data-ttu-id="7a636-111">`SetPriority`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7a636-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="7a636-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7a636-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7a636-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7a636-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7a636-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7a636-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7a636-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7a636-115">The call timed out.</span></span>|  
|<span data-ttu-id="7a636-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7a636-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7a636-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="7a636-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7a636-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7a636-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7a636-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="7a636-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7a636-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7a636-120">E_FAIL</span></span>|<span data-ttu-id="7a636-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7a636-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7a636-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7a636-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7a636-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7a636-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a636-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a636-124">Remarks</span></span>  
 <span data-ttu-id="7a636-125">Vlákna jsou uděleno zpracování přihlášení pomocí kruhového dotazování systém, který je částečně založená na úroveň priority vlákno.</span><span class="sxs-lookup"><span data-stu-id="7a636-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="7a636-126">`SetPriority`Umožňuje CLR nastavit úroveň priority tento přístup z více vláken pro aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="7a636-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="7a636-127">Následující `newPriority` hodnoty jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="7a636-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="7a636-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7a636-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="7a636-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7a636-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="7a636-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="7a636-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="7a636-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="7a636-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="7a636-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="7a636-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="7a636-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7a636-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="7a636-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="7a636-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="7a636-135">Volání CLR `SetPriority` při hodnotu <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> se mění pomocí uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="7a636-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="7a636-136">Hostitel můžete definovat vlastní algoritmy pro přístup z více vláken s prioritou přiřazení a může tuto žádost ignorovat.</span><span class="sxs-lookup"><span data-stu-id="7a636-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a636-137">`SetPriority`nevytváří sestavu zda byl změněn úroveň priority přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="7a636-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="7a636-138">Volání [ihosttask::getpriority –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) k určení hodnoty úroveň priority úkolu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="7a636-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="7a636-139">Přístup z více vláken s prioritou úrovně hodnoty jsou definovány Win32 `SetThreadPriority` funkce.</span><span class="sxs-lookup"><span data-stu-id="7a636-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="7a636-140">Další informace o priorita vlákna naleznete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="7a636-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a636-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a636-141">Requirements</span></span>  
 <span data-ttu-id="7a636-142">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a636-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a636-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a636-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a636-144">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a636-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a636-145">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a636-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a636-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a636-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="7a636-147">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a636-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7a636-148">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a636-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7a636-149">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a636-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7a636-150">Getpriority – metoda</span><span class="sxs-lookup"><span data-stu-id="7a636-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="7a636-151">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a636-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
