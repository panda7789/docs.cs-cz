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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 983cad5ed87d0666ed71a805a3b3f7a3c7e7c091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444301"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="20029-102">IHostTaskManager::CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="20029-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="20029-103">Umožňuje zadat, zda modul CLR (CLR) můžete vložené zadaný volání nespravovaného funkce hostiteli.</span><span class="sxs-lookup"><span data-stu-id="20029-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20029-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20029-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20029-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20029-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="20029-106">[v] Adresa v rámci tohoto souboru namapované přenosné spustitelný soubor (PE) nespravované funkce, které má být volána.</span><span class="sxs-lookup"><span data-stu-id="20029-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="20029-107">[out] Ukazatel na logickou hodnotu, která určuje, zda hostitel vyžaduje volání jazyka.</span><span class="sxs-lookup"><span data-stu-id="20029-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20029-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="20029-108">Return Value</span></span>  
  
|<span data-ttu-id="20029-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20029-109">HRESULT</span></span>|<span data-ttu-id="20029-110">Popis</span><span class="sxs-lookup"><span data-stu-id="20029-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20029-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="20029-111">S_OK</span></span>|<span data-ttu-id="20029-112">`CallNeedsHostHook` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="20029-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="20029-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20029-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20029-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="20029-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20029-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20029-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20029-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="20029-116">The call timed out.</span></span>|  
|<span data-ttu-id="20029-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20029-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20029-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="20029-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20029-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20029-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20029-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="20029-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20029-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20029-121">E_FAIL</span></span>|<span data-ttu-id="20029-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="20029-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="20029-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="20029-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20029-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="20029-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20029-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20029-125">Remarks</span></span>  
 <span data-ttu-id="20029-126">Pro optimalizaci provádění kódu, modul CLR provede analýzu pro každou platformu vyvolání volání během kompilace k určení, zda může být vložená volání.</span><span class="sxs-lookup"><span data-stu-id="20029-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="20029-127">`CallNeedsHostHook` Umožňuje hostitele k přepsání tohoto rozhodnutí tím, že vyžaduje, aby volání nespravovaného funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="20029-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="20029-128">Pokud hostitel vyžaduje háku, modul runtime nemá volání mimo řádek.</span><span class="sxs-lookup"><span data-stu-id="20029-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="20029-129">Hostitel obvykle by vyžadovaly háku tam, kde je nutné upravit s plovoucí desetinnou čárkou stavu, nebo po přijetí oznámení, že volání přechází do stavu, kde hostitele nemůže sledovat požadavky modulu runtime paměti nebo všechny zámky prováděné.</span><span class="sxs-lookup"><span data-stu-id="20029-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="20029-130">Pokud hostitel vyžaduje, aby volání jazyka, modul runtime upozorní hostiteli přechody do a ze spravovaného kódu pomocí volání [enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ Reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), a [reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="20029-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20029-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20029-131">Requirements</span></span>  
 <span data-ttu-id="20029-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20029-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20029-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20029-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20029-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20029-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20029-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20029-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20029-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="20029-136">See Also</span></span>  
 [<span data-ttu-id="20029-137">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20029-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="20029-138">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20029-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="20029-139">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20029-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="20029-140">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20029-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
