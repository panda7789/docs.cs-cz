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
ms.openlocfilehash: f5a595651baa48553997c2cba138f4f61bd530f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133091"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="6bae7-102">IHostTaskManager::CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="6bae7-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="6bae7-103">Umožňuje hostiteli určit, zda může modul CLR (Common Language Runtime) vložit zadané volání do nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="6bae7-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bae7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bae7-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bae7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bae7-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="6bae7-106">pro Adresa v mapovaném souboru přenositelného spustitelného souboru (PE) nespravované funkce, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="6bae7-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="6bae7-107">mimo Ukazatel na logickou hodnotu, která označuje, zda hostitel vyžaduje, aby volání bylo zavěšeno.</span><span class="sxs-lookup"><span data-stu-id="6bae7-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bae7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bae7-108">Return Value</span></span>  
  
|<span data-ttu-id="6bae7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bae7-109">HRESULT</span></span>|<span data-ttu-id="6bae7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6bae7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6bae7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bae7-111">S_OK</span></span>|<span data-ttu-id="6bae7-112">`CallNeedsHostHook` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6bae7-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="6bae7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6bae7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6bae7-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6bae7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6bae7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6bae7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6bae7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6bae7-116">The call timed out.</span></span>|  
|<span data-ttu-id="6bae7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6bae7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6bae7-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6bae7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6bae7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6bae7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6bae7-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6bae7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6bae7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6bae7-121">E_FAIL</span></span>|<span data-ttu-id="6bae7-122">Došlo k neznámé závažnosti selhání.</span><span class="sxs-lookup"><span data-stu-id="6bae7-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="6bae7-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6bae7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6bae7-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6bae7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bae7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bae7-125">Remarks</span></span>  
 <span data-ttu-id="6bae7-126">Pro usnadnění optimalizace provádění kódu provede modul CLR analýzu volání vyvolání každé platformy během kompilace, aby bylo možné určit, zda lze volání vložit do řádku.</span><span class="sxs-lookup"><span data-stu-id="6bae7-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="6bae7-127">`CallNeedsHostHook` umožňuje hostiteli toto rozhodnutí přepsat tím, že vyžaduje, aby se zavolalo volání nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="6bae7-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="6bae7-128">Pokud hostitel vyžaduje zavěšení, modul runtime nevloží volání.</span><span class="sxs-lookup"><span data-stu-id="6bae7-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="6bae7-129">Hostitel obvykle vyžaduje zavěšení, kde musí upravit stav s plovoucí desetinnou čárkou, nebo po přijetí oznámení, že volání zadává stav, kde hostitel nemůže sledovat požadavky na paměť v modulu runtime nebo jakékoli zámky.</span><span class="sxs-lookup"><span data-stu-id="6bae7-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="6bae7-130">Pokud hostitel vyžaduje, aby bylo volání zavěšeno, modul runtime upozorní hostitele přechodů do a ze spravovaného kódu pomocí volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)a [ReverseLeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="6bae7-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bae7-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bae7-131">Requirements</span></span>  
 <span data-ttu-id="6bae7-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bae7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bae7-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6bae7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bae7-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bae7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bae7-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bae7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bae7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bae7-136">See also</span></span>

- [<span data-ttu-id="6bae7-137">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bae7-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6bae7-138">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bae7-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6bae7-139">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bae7-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6bae7-140">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bae7-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
