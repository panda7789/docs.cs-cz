---
title: ICLRPolicyManager::SetTimeoutAndAction – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 3a58664a7dc81059214246b53cf967b50cd61063
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140737"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="e844b-102">ICLRPolicyManager::SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="e844b-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="e844b-103">Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu operace.</span><span class="sxs-lookup"><span data-stu-id="e844b-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e844b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e844b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e844b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e844b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e844b-106">pro Jedna z hodnot [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) s informacemi o operaci, pro kterou chcete nastavit časový limit a `action`zásad.</span><span class="sxs-lookup"><span data-stu-id="e844b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="e844b-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e844b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="e844b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e844b-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="e844b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e844b-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="e844b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e844b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="e844b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e844b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="e844b-112">pro Nová hodnota časového limitu v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="e844b-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="e844b-113">Hodnota nekonečných příčin `operation` nikdy nevypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="e844b-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="e844b-114">pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , která označuje akci zásad, kterou by měl modul CLR provést, když dojde k `operation`.</span><span class="sxs-lookup"><span data-stu-id="e844b-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e844b-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e844b-115">Return Value</span></span>  
  
|<span data-ttu-id="e844b-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e844b-116">HRESULT</span></span>|<span data-ttu-id="e844b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e844b-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e844b-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="e844b-118">S_OK</span></span>|<span data-ttu-id="e844b-119">`SetTimeoutAndAction` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e844b-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="e844b-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e844b-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e844b-121">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e844b-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e844b-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e844b-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e844b-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e844b-123">The call timed out.</span></span>|  
|<span data-ttu-id="e844b-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e844b-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e844b-125">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e844b-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e844b-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e844b-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e844b-127">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e844b-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e844b-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e844b-128">E_FAIL</span></span>|<span data-ttu-id="e844b-129">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e844b-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e844b-130">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e844b-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e844b-131">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e844b-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e844b-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e844b-132">E_INVALIDARG</span></span>|<span data-ttu-id="e844b-133">Pro zadaný `operation`nelze nastavit časový limit nebo byla zadána neplatná hodnota pro `action`.</span><span class="sxs-lookup"><span data-stu-id="e844b-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e844b-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e844b-134">Remarks</span></span>  
 <span data-ttu-id="e844b-135">`SetTimeoutAndAction` zapouzdřuje možnosti metod [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) a [ICLRPolicyManager:: SetActionOnTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) a lze je volat místo sekvenčních volání těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="e844b-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e844b-136">Ne všechny hodnoty akcí zásad lze zadat jako časový limit pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="e844b-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e844b-137">Platné hodnoty najdete v částech poznámky v tématech pro tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="e844b-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e844b-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e844b-138">Requirements</span></span>  
 <span data-ttu-id="e844b-139">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e844b-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e844b-140">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e844b-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e844b-141">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e844b-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e844b-142">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e844b-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e844b-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e844b-143">See also</span></span>

- [<span data-ttu-id="e844b-144">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="e844b-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="e844b-145">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="e844b-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="e844b-146">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e844b-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="e844b-147">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="e844b-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="e844b-148">ICLRPolicyManager:: Settimeoutandaction –</span><span class="sxs-lookup"><span data-stu-id="e844b-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
