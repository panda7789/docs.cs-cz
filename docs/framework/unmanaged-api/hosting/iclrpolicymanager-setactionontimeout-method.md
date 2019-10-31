---
title: ICLRPolicyManager::SetActionOnTimeout – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 9ef906ed5e8a6985c084741bf06b683da79c546e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140789"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="c3478-102">ICLRPolicyManager::SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="c3478-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="c3478-103">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést po vypršení časového limitu dané operace.</span><span class="sxs-lookup"><span data-stu-id="c3478-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3478-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3478-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3478-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3478-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="c3478-106">pro Jedna z hodnot [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) označující operaci, pro kterou chcete zadat akci Timeout.</span><span class="sxs-lookup"><span data-stu-id="c3478-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="c3478-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c3478-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="c3478-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c3478-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="c3478-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c3478-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="c3478-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c3478-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="c3478-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c3478-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="c3478-112">pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , která označuje akci zásady, která se má provést, když vyprší časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="c3478-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3478-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3478-113">Return Value</span></span>  
  
|<span data-ttu-id="c3478-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3478-114">HRESULT</span></span>|<span data-ttu-id="c3478-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c3478-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3478-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3478-116">S_OK</span></span>|<span data-ttu-id="c3478-117">`SetActionOnTimeout` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c3478-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="c3478-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c3478-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c3478-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c3478-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c3478-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c3478-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c3478-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c3478-121">The call timed out.</span></span>|  
|<span data-ttu-id="c3478-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c3478-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c3478-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c3478-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c3478-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c3478-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c3478-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c3478-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c3478-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c3478-126">E_FAIL</span></span>|<span data-ttu-id="c3478-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c3478-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c3478-128">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c3478-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c3478-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c3478-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c3478-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c3478-130">E_INVALIDARG</span></span>|<span data-ttu-id="c3478-131">Pro zadaný `operation`nelze nastavit časový limit nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="c3478-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3478-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3478-132">Remarks</span></span>  
 <span data-ttu-id="c3478-133">Hodnota časového limitu může být buď výchozí časový limit nastavený modulem CLR, nebo hodnota zadaná hostitelem ve volání metody [ICLRPolicyManager:: setTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3478-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="c3478-134">Ne všechny hodnoty akcí zásad lze zadat jako časový limit pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="c3478-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="c3478-135">`SetActionOnTimeout` se obvykle používá pouze k eskalaci chování.</span><span class="sxs-lookup"><span data-stu-id="c3478-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="c3478-136">Například hostitel může určit, že je přerušeno přerušování vlákna na hrubé, ale nemůže určit opak.</span><span class="sxs-lookup"><span data-stu-id="c3478-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="c3478-137">Následující tabulka popisuje platné hodnoty `action` pro platné hodnoty `operation`.</span><span class="sxs-lookup"><span data-stu-id="c3478-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="c3478-138">Hodnota pro `operation`</span><span class="sxs-lookup"><span data-stu-id="c3478-138">Value for `operation`</span></span>|<span data-ttu-id="c3478-139">Platné hodnoty pro `action`</span><span class="sxs-lookup"><span data-stu-id="c3478-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="c3478-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c3478-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="c3478-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="c3478-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="c3478-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="c3478-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="c3478-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c3478-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c3478-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c3478-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c3478-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-145">-   eExitProcess</span></span><br /><span data-ttu-id="c3478-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="c3478-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c3478-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c3478-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c3478-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="c3478-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="c3478-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c3478-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="c3478-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c3478-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="c3478-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-152">-   eExitProcess</span></span><br /><span data-ttu-id="c3478-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="c3478-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c3478-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c3478-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="c3478-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="c3478-156">OPR_ProcessExit</span></span>|<span data-ttu-id="c3478-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-157">-   eExitProcess</span></span><br /><span data-ttu-id="c3478-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="c3478-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="c3478-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="c3478-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="c3478-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3478-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3478-161">Requirements</span></span>  
 <span data-ttu-id="c3478-162">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3478-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3478-163">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3478-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3478-164">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3478-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3478-165">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3478-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3478-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3478-166">See also</span></span>

- [<span data-ttu-id="c3478-167">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="c3478-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="c3478-168">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="c3478-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="c3478-169">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3478-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c3478-170">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3478-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
