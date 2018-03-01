---
title: "IHostTaskManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="d0e46-102">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0e46-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="d0e46-103">Poskytuje metody, které povolit modul CLR (CLR) pro práci s úkoly prostřednictvím hostitele místo použití funkce dělení na vlákna nebo fiber standardní operační systém.</span><span class="sxs-lookup"><span data-stu-id="d0e46-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0e46-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d0e46-104">Methods</span></span>  
  
|<span data-ttu-id="d0e46-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-105">Method</span></span>|<span data-ttu-id="d0e46-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d0e46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0e46-107">BeginDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="d0e46-108">Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí přerušil aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="d0e46-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="d0e46-109">BeginThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="d0e46-110">Upozorní, že hostitele, který spravovaný kód je zadání období, ve kterém nesmí být aktuální úlohy přesunout do jiné vlákno operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d0e46-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="d0e46-111">CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="d0e46-112">Umožňuje zadat, zda modul common language runtime můžete vložené zadaný volání nespravovaného funkce hostiteli.</span><span class="sxs-lookup"><span data-stu-id="d0e46-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="d0e46-113">CreateTask – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="d0e46-114">Požadavky, že hostitel vytvořit novou úlohu.</span><span class="sxs-lookup"><span data-stu-id="d0e46-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="d0e46-115">EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="d0e46-116">Upozorní hostitele, který je spravovaný kód je ukončení období, ve kterém nesmí být aktuální úloha byla přerušena, následující starší volání `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="d0e46-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="d0e46-117">EndThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="d0e46-118">Upozorní hostitele, který je spravovaný kód je ukončení období, ve kterém nesmí být aktuální úlohy přesunout do jiné vlákno operačního systému, následující starší volání `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="d0e46-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="d0e46-119">EnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="d0e46-120">Upozorní hostitele, že volání pro metodu nespravované, jako je platforma vyvolání metody vrací řízení provádění modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d0e46-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="d0e46-121">GetCurrentTask – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="d0e46-122">Získá ukazatele rozhraní pro úlohu, která je aktuálně spuštěných ve vláknu operačního systému, ze kterého přišla tato žádost.</span><span class="sxs-lookup"><span data-stu-id="d0e46-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="d0e46-123">GetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="d0e46-124">Získá velikost zásobníku místa, které se musí být k dispozici po dokončení operace zásobníku, ale před zavřením procesu.</span><span class="sxs-lookup"><span data-stu-id="d0e46-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="d0e46-125">LeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="d0e46-126">Upozorní, že hostitele, který spravovaného kódu se chystá provést volání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="d0e46-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="d0e46-127">ReverseEnterRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="d0e46-128">Upozorní hostitele, že se provádí volání do common language runtime (CLR) z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d0e46-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="d0e46-129">ReverseLeaveRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="d0e46-130">Hostitel upozorní, že je ovládací prvek ponechat modulu CLR a zadáním nespravované funkci, která byla, pak volané ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d0e46-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="d0e46-131">SetCLRTaskManager – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="d0e46-132">Poskytuje ukazatele rozhraní na hostiteli [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d0e46-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="d0e46-133">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="d0e46-134">Upozorní hostitele, že modulu CLR se změnila národního prostředí na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="d0e46-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="d0e46-135">SetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="d0e46-136">Vyhrazeno pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="d0e46-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="d0e46-137">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="d0e46-138">Upozorní hostitele, národní prostředí uživatelského rozhraní se změnil na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="d0e46-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="d0e46-139">Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="d0e46-140">Upozorní hostitele, že aktuální úlohy přechází do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="d0e46-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="d0e46-141">SwitchToTask – metoda</span><span class="sxs-lookup"><span data-stu-id="d0e46-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="d0e46-142">Upozorní hostitele, musí přepnout na aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="d0e46-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0e46-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0e46-143">Remarks</span></span>  
 <span data-ttu-id="d0e46-144">`IHostTaskManager`Umožňuje CLR vytvořit a spravovat úlohy, k poskytování háky pro hostitele zásah, kdy dojde k řízení přenosu ze spravovaného na nespravovaný kód a naopak a chcete zadat některé akce hostitele může a nelze provést během provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="d0e46-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e46-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0e46-145">Requirements</span></span>  
 <span data-ttu-id="d0e46-146">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0e46-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e46-147">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0e46-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0e46-148">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0e46-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0e46-149">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e46-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e46-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0e46-150">See Also</span></span>  
 [<span data-ttu-id="d0e46-151">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0e46-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d0e46-152">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0e46-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d0e46-153">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0e46-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d0e46-154">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d0e46-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
