---
title: "ICLRPolicyManager::SetActionOnFailure – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnFailure
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5dc8e27ed1a5701886c3583a7515e4212f490208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="c974d-102">ICLRPolicyManager::SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="c974d-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="c974d-103">Určuje akci zásady, které modul CLR (CLR) má provést, pokud dojde k selhání zadané.</span><span class="sxs-lookup"><span data-stu-id="c974d-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c974d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c974d-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c974d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c974d-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="c974d-106">[v] Jeden z [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty, která určuje typ selhání, pro které chcete provést akci.</span><span class="sxs-lookup"><span data-stu-id="c974d-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="c974d-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci, která mají být provedeny, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="c974d-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="c974d-108">Seznam podporovaných hodnot najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="c974d-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c974d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c974d-109">Return Value</span></span>  
  
|<span data-ttu-id="c974d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c974d-110">HRESULT</span></span>|<span data-ttu-id="c974d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c974d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c974d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c974d-112">S_OK</span></span>|<span data-ttu-id="c974d-113">`SetActionOnFailure`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c974d-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="c974d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c974d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c974d-115">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c974d-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c974d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c974d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c974d-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c974d-117">The call timed out.</span></span>|  
|<span data-ttu-id="c974d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c974d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c974d-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c974d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c974d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c974d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c974d-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c974d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c974d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c974d-122">E_FAIL</span></span>|<span data-ttu-id="c974d-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c974d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c974d-124">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c974d-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c974d-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c974d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c974d-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c974d-126">E_INVALIDARG</span></span>|<span data-ttu-id="c974d-127">Akce zásad nelze nastavit pro zadanou operaci, nebo pro operaci byla zadána neplatná zásada akce.</span><span class="sxs-lookup"><span data-stu-id="c974d-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c974d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c974d-128">Remarks</span></span>  
 <span data-ttu-id="c974d-129">Ve výchozím modulu CLR vyvolá výjimku, když se nepodaří přidělení prostředků, třeba paměť.</span><span class="sxs-lookup"><span data-stu-id="c974d-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="c974d-130">`SetActionOnFailure`umožňuje hostiteli, aby toto chování potlačit zadáním zásad akce provést při selhání.</span><span class="sxs-lookup"><span data-stu-id="c974d-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="c974d-131">V následující tabulce jsou uvedeny kombinace [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) a [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c974d-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="c974d-132">(Je vynechaný předponu FAIL_ [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="c974d-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="c974d-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="c974d-133">NonCriticalResource</span></span>|<span data-ttu-id="c974d-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="c974d-134">CriticalResource</span></span>|<span data-ttu-id="c974d-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="c974d-135">FatalRuntime</span></span>|<span data-ttu-id="c974d-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="c974d-136">OrphanedLock</span></span>|<span data-ttu-id="c974d-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="c974d-137">StackOverflow</span></span>|<span data-ttu-id="c974d-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="c974d-138">AccessViolation</span></span>|<span data-ttu-id="c974d-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="c974d-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="c974d-140">X</span><span class="sxs-lookup"><span data-stu-id="c974d-140">X</span></span>|<span data-ttu-id="c974d-141">X</span><span class="sxs-lookup"><span data-stu-id="c974d-141">X</span></span>||||<span data-ttu-id="c974d-142">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-142">N/A</span></span>||  
|<span data-ttu-id="c974d-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="c974d-143">eThrowException</span></span>|<span data-ttu-id="c974d-144">X</span><span class="sxs-lookup"><span data-stu-id="c974d-144">X</span></span>|<span data-ttu-id="c974d-145">X</span><span class="sxs-lookup"><span data-stu-id="c974d-145">X</span></span>||||<span data-ttu-id="c974d-146">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="c974d-147">X</span><span class="sxs-lookup"><span data-stu-id="c974d-147">X</span></span>|<span data-ttu-id="c974d-148">X</span><span class="sxs-lookup"><span data-stu-id="c974d-148">X</span></span>||||<span data-ttu-id="c974d-149">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-149">N/A</span></span>|<span data-ttu-id="c974d-150">X</span><span class="sxs-lookup"><span data-stu-id="c974d-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="c974d-151">X</span><span class="sxs-lookup"><span data-stu-id="c974d-151">X</span></span>|<span data-ttu-id="c974d-152">X</span><span class="sxs-lookup"><span data-stu-id="c974d-152">X</span></span>||||<span data-ttu-id="c974d-153">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-153">N/A</span></span>|<span data-ttu-id="c974d-154">X</span><span class="sxs-lookup"><span data-stu-id="c974d-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="c974d-155">X</span><span class="sxs-lookup"><span data-stu-id="c974d-155">X</span></span>|<span data-ttu-id="c974d-156">X</span><span class="sxs-lookup"><span data-stu-id="c974d-156">X</span></span>||<span data-ttu-id="c974d-157">X</span><span class="sxs-lookup"><span data-stu-id="c974d-157">X</span></span>||<span data-ttu-id="c974d-158">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-158">N/A</span></span>|<span data-ttu-id="c974d-159">X</span><span class="sxs-lookup"><span data-stu-id="c974d-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="c974d-160">X</span><span class="sxs-lookup"><span data-stu-id="c974d-160">X</span></span>|<span data-ttu-id="c974d-161">X</span><span class="sxs-lookup"><span data-stu-id="c974d-161">X</span></span>||<span data-ttu-id="c974d-162">X</span><span class="sxs-lookup"><span data-stu-id="c974d-162">X</span></span>|<span data-ttu-id="c974d-163">X</span><span class="sxs-lookup"><span data-stu-id="c974d-163">X</span></span>|<span data-ttu-id="c974d-164">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-164">N/A</span></span>|<span data-ttu-id="c974d-165">X</span><span class="sxs-lookup"><span data-stu-id="c974d-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="c974d-166">X</span><span class="sxs-lookup"><span data-stu-id="c974d-166">X</span></span>|<span data-ttu-id="c974d-167">X</span><span class="sxs-lookup"><span data-stu-id="c974d-167">X</span></span>||<span data-ttu-id="c974d-168">X</span><span class="sxs-lookup"><span data-stu-id="c974d-168">X</span></span>|<span data-ttu-id="c974d-169">X</span><span class="sxs-lookup"><span data-stu-id="c974d-169">X</span></span>|<span data-ttu-id="c974d-170">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-170">N/A</span></span>|<span data-ttu-id="c974d-171">X</span><span class="sxs-lookup"><span data-stu-id="c974d-171">X</span></span>|  
|<span data-ttu-id="c974d-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="c974d-172">eFastExitProcess</span></span>|<span data-ttu-id="c974d-173">X</span><span class="sxs-lookup"><span data-stu-id="c974d-173">X</span></span>|<span data-ttu-id="c974d-174">X</span><span class="sxs-lookup"><span data-stu-id="c974d-174">X</span></span>||<span data-ttu-id="c974d-175">X</span><span class="sxs-lookup"><span data-stu-id="c974d-175">X</span></span>|<span data-ttu-id="c974d-176">X</span><span class="sxs-lookup"><span data-stu-id="c974d-176">X</span></span>|<span data-ttu-id="c974d-177">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="c974d-178">X</span><span class="sxs-lookup"><span data-stu-id="c974d-178">X</span></span>|<span data-ttu-id="c974d-179">X</span><span class="sxs-lookup"><span data-stu-id="c974d-179">X</span></span>|<span data-ttu-id="c974d-180">X</span><span class="sxs-lookup"><span data-stu-id="c974d-180">X</span></span>|<span data-ttu-id="c974d-181">X</span><span class="sxs-lookup"><span data-stu-id="c974d-181">X</span></span>|<span data-ttu-id="c974d-182">X</span><span class="sxs-lookup"><span data-stu-id="c974d-182">X</span></span>|<span data-ttu-id="c974d-183">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="c974d-184">X</span><span class="sxs-lookup"><span data-stu-id="c974d-184">X</span></span>|<span data-ttu-id="c974d-185">X</span><span class="sxs-lookup"><span data-stu-id="c974d-185">X</span></span>|<span data-ttu-id="c974d-186">X</span><span class="sxs-lookup"><span data-stu-id="c974d-186">X</span></span>|<span data-ttu-id="c974d-187">X</span><span class="sxs-lookup"><span data-stu-id="c974d-187">X</span></span>|<span data-ttu-id="c974d-188">X</span><span class="sxs-lookup"><span data-stu-id="c974d-188">X</span></span>|<span data-ttu-id="c974d-189">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="c974d-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="c974d-190">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c974d-190">Requirements</span></span>  
 <span data-ttu-id="c974d-191">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c974d-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c974d-192">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c974d-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c974d-193">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c974d-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c974d-194">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c974d-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c974d-195">Viz také</span><span class="sxs-lookup"><span data-stu-id="c974d-195">See Also</span></span>  
 [<span data-ttu-id="c974d-196">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="c974d-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="c974d-197">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="c974d-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="c974d-198">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c974d-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="c974d-199">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c974d-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
