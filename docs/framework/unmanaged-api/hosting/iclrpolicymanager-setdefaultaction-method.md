---
title: "ICLRPolicyManager::SetDefaultAction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751853aaf4322c15b44bb9b912d293a081c24ba8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="afd9d-102">ICLRPolicyManager::SetDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="afd9d-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="afd9d-103">Určuje akci zásady, které modul CLR (CLR) má provést, pokud dojde k zadané operace.</span><span class="sxs-lookup"><span data-stu-id="afd9d-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afd9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afd9d-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afd9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afd9d-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="afd9d-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, který udává akci, pro které CLR lze přizpůsobit chování.</span><span class="sxs-lookup"><span data-stu-id="afd9d-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="afd9d-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, indikující akce zásad modulu CLR by měla provést v případě `operation` dojde.</span><span class="sxs-lookup"><span data-stu-id="afd9d-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afd9d-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="afd9d-108">Return Value</span></span>  
  
|<span data-ttu-id="afd9d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afd9d-109">HRESULT</span></span>|<span data-ttu-id="afd9d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="afd9d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afd9d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="afd9d-111">S_OK</span></span>|<span data-ttu-id="afd9d-112">`SetDefaultAction`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="afd9d-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="afd9d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="afd9d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="afd9d-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="afd9d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="afd9d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="afd9d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="afd9d-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="afd9d-116">The call timed out.</span></span>|  
|<span data-ttu-id="afd9d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="afd9d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="afd9d-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="afd9d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="afd9d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="afd9d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="afd9d-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="afd9d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="afd9d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="afd9d-121">E_FAIL</span></span>|<span data-ttu-id="afd9d-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="afd9d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="afd9d-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="afd9d-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="afd9d-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="afd9d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="afd9d-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="afd9d-125">E_INVALIDARG</span></span>|<span data-ttu-id="afd9d-126">Neplatný `action` byl zadán pro `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="afd9d-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afd9d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afd9d-127">Remarks</span></span>  
 <span data-ttu-id="afd9d-128">Ne všechny akce hodnoty zásad lze zadat jako výchozí chování v operacích modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="afd9d-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="afd9d-129">`SetDefaultAction`obvykle slouží pouze pro zvýšení chování.</span><span class="sxs-lookup"><span data-stu-id="afd9d-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="afd9d-130">Například hostitel můžete určit, že vlákno přerušení být převedena na článku neslušní vláken přerušení, ale nelze zadat jako opak.</span><span class="sxs-lookup"><span data-stu-id="afd9d-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="afd9d-131">Následující tabulka popisuje platném `action` hodnoty pro každé možné `operation` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="afd9d-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="afd9d-132">Hodnota pro`operation`</span><span class="sxs-lookup"><span data-stu-id="afd9d-132">Value for `operation`</span></span>|<span data-ttu-id="afd9d-133">Platné hodnoty pro`action`</span><span class="sxs-lookup"><span data-stu-id="afd9d-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="afd9d-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="afd9d-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="afd9d-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="afd9d-135">-   eAbortThread</span></span><br /><span data-ttu-id="afd9d-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="afd9d-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="afd9d-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-139">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="afd9d-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="afd9d-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="afd9d-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="afd9d-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="afd9d-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="afd9d-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="afd9d-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-148">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="afd9d-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="afd9d-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="afd9d-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-155">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="afd9d-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="afd9d-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="afd9d-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-161">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="afd9d-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="afd9d-165">OPR_ProcessExit</span></span>|<span data-ttu-id="afd9d-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-166">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="afd9d-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="afd9d-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="afd9d-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="afd9d-171">-   eNoAction</span></span><br /><span data-ttu-id="afd9d-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="afd9d-172">-   eAbortThread</span></span><br /><span data-ttu-id="afd9d-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="afd9d-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="afd9d-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="afd9d-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="afd9d-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-176">-   eExitProcess</span></span><br /><span data-ttu-id="afd9d-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="afd9d-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="afd9d-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="afd9d-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="afd9d-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afd9d-180">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afd9d-180">Requirements</span></span>  
 <span data-ttu-id="afd9d-181">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afd9d-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afd9d-182">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="afd9d-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afd9d-183">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afd9d-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afd9d-184">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afd9d-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd9d-185">Viz také</span><span class="sxs-lookup"><span data-stu-id="afd9d-185">See Also</span></span>  
 [<span data-ttu-id="afd9d-186">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="afd9d-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="afd9d-187">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="afd9d-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="afd9d-188">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afd9d-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
