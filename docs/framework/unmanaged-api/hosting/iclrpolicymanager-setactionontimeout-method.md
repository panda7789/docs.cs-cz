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
ms.openlocfilehash: 0b8e7dfbe377e60b548003af10fb11392b514030
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703450"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="e0be0-102">ICLRPolicyManager::SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="e0be0-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="e0be0-103">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést po vypršení časového limitu dané operace.</span><span class="sxs-lookup"><span data-stu-id="e0be0-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0be0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0be0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0be0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0be0-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e0be0-106">pro Jedna z hodnot [EClrOperation –](eclroperation-enumeration.md) označující operaci, pro kterou chcete zadat akci Timeout.</span><span class="sxs-lookup"><span data-stu-id="e0be0-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="e0be0-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e0be0-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="e0be0-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e0be0-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="e0be0-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e0be0-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="e0be0-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0be0-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="e0be0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0be0-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="e0be0-112">pro Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) , která označuje akci zásady, která se má provést, když vyprší časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="e0be0-112">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0be0-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0be0-113">Return Value</span></span>  
  
|<span data-ttu-id="e0be0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0be0-114">HRESULT</span></span>|<span data-ttu-id="e0be0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e0be0-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0be0-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0be0-116">S_OK</span></span>|<span data-ttu-id="e0be0-117">`SetActionOnTimeout`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e0be0-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="e0be0-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0be0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0be0-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e0be0-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0be0-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0be0-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0be0-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e0be0-121">The call timed out.</span></span>|  
|<span data-ttu-id="e0be0-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0be0-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0be0-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e0be0-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0be0-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0be0-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0be0-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e0be0-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0be0-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0be0-126">E_FAIL</span></span>|<span data-ttu-id="e0be0-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e0be0-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0be0-128">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="e0be0-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0be0-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0be0-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0be0-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e0be0-130">E_INVALIDARG</span></span>|<span data-ttu-id="e0be0-131">Pro zadanou hodnotu nelze nastavit časový limit `operation` nebo byla zadána neplatná hodnota pro `operation` .</span><span class="sxs-lookup"><span data-stu-id="e0be0-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0be0-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0be0-132">Remarks</span></span>  
 <span data-ttu-id="e0be0-133">Hodnota časového limitu může být buď výchozí časový limit nastavený modulem CLR, nebo hodnota zadaná hostitelem ve volání metody [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0be0-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="e0be0-134">Ne všechny hodnoty akcí zásad lze zadat jako časový limit pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="e0be0-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="e0be0-135">`SetActionOnTimeout`se obvykle používá pouze k eskalaci chování.</span><span class="sxs-lookup"><span data-stu-id="e0be0-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="e0be0-136">Například hostitel může určit, že je přerušeno přerušování vlákna na hrubé, ale nemůže určit opak.</span><span class="sxs-lookup"><span data-stu-id="e0be0-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e0be0-137">Následující tabulka popisuje platné `action` hodnoty platných `operation` hodnot.</span><span class="sxs-lookup"><span data-stu-id="e0be0-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="e0be0-138">Hodnota pro`operation`</span><span class="sxs-lookup"><span data-stu-id="e0be0-138">Value for `operation`</span></span>|<span data-ttu-id="e0be0-139">Platné hodnoty pro`action`</span><span class="sxs-lookup"><span data-stu-id="e0be0-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e0be0-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0be0-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e0be0-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e0be0-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e0be0-142">- eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e0be0-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e0be0-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e0be0-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e0be0-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e0be0-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e0be0-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-145">-   eExitProcess</span></span><br /><span data-ttu-id="e0be0-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="e0be0-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e0be0-148">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e0be0-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e0be0-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e0be0-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e0be0-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e0be0-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e0be0-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e0be0-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e0be0-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-152">-   eExitProcess</span></span><br /><span data-ttu-id="e0be0-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="e0be0-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e0be0-155">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e0be0-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e0be0-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e0be0-156">OPR_ProcessExit</span></span>|<span data-ttu-id="e0be0-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-157">-   eExitProcess</span></span><br /><span data-ttu-id="e0be0-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="e0be0-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e0be0-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e0be0-160">- eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e0be0-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0be0-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0be0-161">Requirements</span></span>  
 <span data-ttu-id="e0be0-162">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0be0-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0be0-163">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0be0-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0be0-164">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0be0-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0be0-165">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0be0-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0be0-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0be0-166">See also</span></span>

- [<span data-ttu-id="e0be0-167">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="e0be0-167">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="e0be0-168">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="e0be0-168">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="e0be0-169">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0be0-169">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e0be0-170">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0be0-170">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
