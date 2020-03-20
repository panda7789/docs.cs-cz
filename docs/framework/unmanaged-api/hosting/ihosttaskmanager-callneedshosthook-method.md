---
title: IHostTaskManager::CallNeedsHostHook – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176289"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="ab857-102">IHostTaskManager::CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="ab857-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="ab857-103">Umožňuje hostiteli určit, zda může zadaný kód CLR vřadit zadaný jazyk do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="ab857-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab857-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab857-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab857-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="ab857-106">[v] Adresa v rámci mapovaného přenosného spustitelného souboru (PE) nespravované funkce, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="ab857-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="ab857-107">[out] Ukazatel na logickou hodnotu, která označuje, zda hostitel vyžaduje, aby volání bylo připojeno.</span><span class="sxs-lookup"><span data-stu-id="ab857-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab857-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab857-108">Return Value</span></span>  
  
|<span data-ttu-id="ab857-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab857-109">HRESULT</span></span>|<span data-ttu-id="ab857-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ab857-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab857-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab857-111">S_OK</span></span>|<span data-ttu-id="ab857-112">`CallNeedsHostHook`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ab857-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="ab857-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ab857-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ab857-114">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ab857-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ab857-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ab857-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ab857-116">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="ab857-116">The call timed out.</span></span>|  
|<span data-ttu-id="ab857-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ab857-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ab857-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ab857-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ab857-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ab857-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ab857-120">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab857-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ab857-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="ab857-121">E_FAIL</span></span>|<span data-ttu-id="ab857-122">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="ab857-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="ab857-123">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ab857-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ab857-124">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ab857-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab857-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab857-125">Remarks</span></span>  
 <span data-ttu-id="ab857-126">Chcete-li optimalizovat spuštění kódu, CLR provede analýzu každé platformy vyvolat volání během kompilace k určení, zda volání může být vložen.</span><span class="sxs-lookup"><span data-stu-id="ab857-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="ab857-127">`CallNeedsHostHook`umožňuje hostiteli přepsat toto rozhodnutí tím, že vyžaduje, aby volání nespravované funkce bylo připojeno.</span><span class="sxs-lookup"><span data-stu-id="ab857-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="ab857-128">Pokud hostitel vyžaduje zavěšení, runtime není vsazení volání.</span><span class="sxs-lookup"><span data-stu-id="ab857-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="ab857-129">Hostitel obvykle bude vyžadovat zavěšení, kde musí upravit stav s plovoucí desetinnou desetinnou hlavou nebo po přijetí oznámení, že volání vstupuje do stavu, kdy hostitel nemůže sledovat požadavky za běhu na paměť nebo všechny přijaté zámky.</span><span class="sxs-lookup"><span data-stu-id="ab857-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="ab857-130">Pokud hostitel vyžaduje, aby bylo volání připojeno, program runtime upozorní hostitele přechodů do a ze spravovaného kódu pomocí volání [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)a [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="ab857-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab857-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab857-131">Requirements</span></span>  
 <span data-ttu-id="ab857-132">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab857-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab857-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab857-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab857-134">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab857-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab857-135">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab857-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab857-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab857-136">See also</span></span>

- [<span data-ttu-id="ab857-137">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab857-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ab857-138">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab857-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ab857-139">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab857-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ab857-140">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab857-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
