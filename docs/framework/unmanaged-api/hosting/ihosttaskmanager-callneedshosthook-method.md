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
ms.openlocfilehash: 9a33f71ef2e0b19a33255f3745ac4d5a84cdf4ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749739"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="9d302-102">IHostTaskManager::CallNeedsHostHook – metoda</span><span class="sxs-lookup"><span data-stu-id="9d302-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="9d302-103">Umožňuje hostiteli k určení, zda modul CLR (CLR) můžete vložené určené volání nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="9d302-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d302-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d302-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d302-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="9d302-106">[in] Adresy v rámci souboru namapované (PE portable executable) nespravované funkci, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="9d302-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="9d302-107">[out] Ukazatel na logickou hodnotu udávající, zda hostitel vyžaduje volání využívat.</span><span class="sxs-lookup"><span data-stu-id="9d302-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d302-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d302-108">Return Value</span></span>  
  
|<span data-ttu-id="9d302-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d302-109">HRESULT</span></span>|<span data-ttu-id="9d302-110">Popis</span><span class="sxs-lookup"><span data-stu-id="9d302-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d302-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d302-111">S_OK</span></span>|<span data-ttu-id="9d302-112">`CallNeedsHostHook` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="9d302-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="9d302-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d302-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d302-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9d302-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d302-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d302-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d302-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9d302-116">The call timed out.</span></span>|  
|<span data-ttu-id="9d302-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d302-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d302-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="9d302-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d302-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d302-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d302-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="9d302-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d302-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d302-121">E_FAIL</span></span>|<span data-ttu-id="9d302-122">Došlo k neznámé závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="9d302-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="9d302-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9d302-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d302-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d302-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d302-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d302-125">Remarks</span></span>  
 <span data-ttu-id="9d302-126">Pro optimalizaci provádění kódu, CLR provádí analýzu pro každou platformu volání funkce invoke během kompilace k určení, zda mohou být vložená volání.</span><span class="sxs-lookup"><span data-stu-id="9d302-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="9d302-127">`CallNeedsHostHook` umožňuje hostiteli přepsat toto rozhodnutí vyžadováním využívat volání nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="9d302-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="9d302-128">Pokud hostitel vyžaduje hák, modul runtime nevloží volání.</span><span class="sxs-lookup"><span data-stu-id="9d302-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="9d302-129">Hostitel obvykle by vyžadovaly hák tam, kde je nutné upravit stav s plovoucí desetinnou čárkou, nebo při přijetí oznámení, že volání přechází do stavu, ve kterém hostitele nelze sledovat modul runtime požadavky na paměť nebo žádné zámky provést.</span><span class="sxs-lookup"><span data-stu-id="9d302-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="9d302-130">Když hostitel vyžaduje využívat volání, modul runtime upozorní hostitele přechody do a ze spravovaného kódu pomocí volání [enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ Reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), a [reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="9d302-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d302-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d302-131">Requirements</span></span>  
 <span data-ttu-id="9d302-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d302-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d302-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d302-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d302-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d302-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d302-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d302-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d302-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d302-136">See also</span></span>

- [<span data-ttu-id="9d302-137">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d302-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9d302-138">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d302-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9d302-139">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d302-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9d302-140">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d302-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
