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
ms.openlocfilehash: 5bc5752d4d2b772b1d18f438c4daaa1b8938da9e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842345"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="1ff91-102">IHostTaskManager::CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="1ff91-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="1ff91-103">Umožňuje hostiteli určit, zda může modul CLR (Common Language Runtime) vložit zadané volání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="1ff91-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ff91-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ff91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ff91-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="1ff91-106">pro Adresa v mapovaném souboru přenositelného spustitelného souboru (PE) nespravované funkce, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="1ff91-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="1ff91-107">mimo Ukazatel na logickou hodnotu, která označuje, zda hostitel vyžaduje, aby volání bylo zavěšeno.</span><span class="sxs-lookup"><span data-stu-id="1ff91-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ff91-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ff91-108">Return Value</span></span>  
  
|<span data-ttu-id="1ff91-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ff91-109">HRESULT</span></span>|<span data-ttu-id="1ff91-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1ff91-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ff91-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ff91-111">S_OK</span></span>|<span data-ttu-id="1ff91-112">`CallNeedsHostHook`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1ff91-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="1ff91-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ff91-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ff91-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1ff91-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ff91-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ff91-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ff91-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1ff91-116">The call timed out.</span></span>|  
|<span data-ttu-id="1ff91-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ff91-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ff91-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="1ff91-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ff91-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ff91-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ff91-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="1ff91-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ff91-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ff91-121">E_FAIL</span></span>|<span data-ttu-id="1ff91-122">Došlo k neznámé závažnosti selhání.</span><span class="sxs-lookup"><span data-stu-id="1ff91-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="1ff91-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="1ff91-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ff91-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ff91-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff91-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ff91-125">Remarks</span></span>  
 <span data-ttu-id="1ff91-126">Pro usnadnění optimalizace provádění kódu provede modul CLR analýzu volání vyvolání každé platformy během kompilace, aby bylo možné určit, zda lze volání vložit do řádku.</span><span class="sxs-lookup"><span data-stu-id="1ff91-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="1ff91-127">`CallNeedsHostHook`umožňuje hostiteli přepsat toto rozhodnutí tím, že vyžaduje, aby se zavolalo volání nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="1ff91-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="1ff91-128">Pokud hostitel vyžaduje zavěšení, modul runtime nevloží volání.</span><span class="sxs-lookup"><span data-stu-id="1ff91-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="1ff91-129">Hostitel obvykle vyžaduje zavěšení, kde musí upravit stav s plovoucí desetinnou čárkou, nebo po přijetí oznámení, že volání zadává stav, kde hostitel nemůže sledovat požadavky na paměť v modulu runtime nebo jakékoli zámky.</span><span class="sxs-lookup"><span data-stu-id="1ff91-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="1ff91-130">Pokud hostitel vyžaduje, aby bylo volání zavěšeno, modul runtime upozorní hostitele přechodů do a ze spravovaného kódu pomocí volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)a [ReverseLeaveRuntime –](ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="1ff91-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff91-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ff91-131">Requirements</span></span>  
 <span data-ttu-id="1ff91-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ff91-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff91-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ff91-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ff91-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ff91-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ff91-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff91-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff91-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ff91-136">See also</span></span>

- [<span data-ttu-id="1ff91-137">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ff91-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1ff91-138">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ff91-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1ff91-139">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ff91-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1ff91-140">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ff91-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
