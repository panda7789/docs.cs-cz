---
title: ICLRPolicyManager::SetActionOnFailure – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638967"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="156f9-102">ICLRPolicyManager::SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="156f9-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="156f9-103">Určuje akci zásad by měl trvat common language runtime (CLR), když dojde k selhání zadané.</span><span class="sxs-lookup"><span data-stu-id="156f9-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="156f9-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="156f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="156f9-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="156f9-106">[in] Jeden z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty určující typ selhání, pro které chcete provést akci.</span><span class="sxs-lookup"><span data-stu-id="156f9-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="156f9-107">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty indikující akce, která má být provedeny, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="156f9-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="156f9-108">Seznam podporovaných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="156f9-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="156f9-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="156f9-109">Return Value</span></span>  
  
|<span data-ttu-id="156f9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="156f9-110">HRESULT</span></span>|<span data-ttu-id="156f9-111">Popis</span><span class="sxs-lookup"><span data-stu-id="156f9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="156f9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="156f9-112">S_OK</span></span>|<span data-ttu-id="156f9-113">`SetActionOnFailure` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="156f9-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="156f9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="156f9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="156f9-115">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="156f9-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="156f9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="156f9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="156f9-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="156f9-117">The call timed out.</span></span>|  
|<span data-ttu-id="156f9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="156f9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="156f9-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="156f9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="156f9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="156f9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="156f9-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="156f9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="156f9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="156f9-122">E_FAIL</span></span>|<span data-ttu-id="156f9-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="156f9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="156f9-124">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="156f9-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="156f9-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="156f9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="156f9-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="156f9-126">E_INVALIDARG</span></span>|<span data-ttu-id="156f9-127">Akce zásad nelze nastavit pro zadanou operaci, nebo byla zadána neplatná zásada akci pro tuto operaci.</span><span class="sxs-lookup"><span data-stu-id="156f9-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="156f9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="156f9-128">Remarks</span></span>  
 <span data-ttu-id="156f9-129">Ve výchozím nastavení CLR vyvolá výjimku, pokud se nezdaří pro přidělení prostředků, jako je paměť.</span><span class="sxs-lookup"><span data-stu-id="156f9-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="156f9-130">`SetActionOnFailure` umožňuje hostiteli toto chování lze přepsat zadáním zásad akce má být provedena po selhání.</span><span class="sxs-lookup"><span data-stu-id="156f9-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="156f9-131">V následující tabulce jsou uvedeny kombinace [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) a [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="156f9-131">The following table shows the combinations of [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="156f9-132">(Předpona FAIL_ je vynecháno z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="156f9-132">(The FAIL_ prefix is omitted from [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="156f9-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="156f9-133">NonCriticalResource</span></span>|<span data-ttu-id="156f9-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="156f9-134">CriticalResource</span></span>|<span data-ttu-id="156f9-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="156f9-135">FatalRuntime</span></span>|<span data-ttu-id="156f9-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="156f9-136">OrphanedLock</span></span>|<span data-ttu-id="156f9-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="156f9-137">StackOverflow</span></span>|<span data-ttu-id="156f9-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="156f9-138">AccessViolation</span></span>|<span data-ttu-id="156f9-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="156f9-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="156f9-140">X</span><span class="sxs-lookup"><span data-stu-id="156f9-140">X</span></span>|<span data-ttu-id="156f9-141">X</span><span class="sxs-lookup"><span data-stu-id="156f9-141">X</span></span>||||<span data-ttu-id="156f9-142">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-142">N/A</span></span>||  
|<span data-ttu-id="156f9-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="156f9-143">eThrowException</span></span>|<span data-ttu-id="156f9-144">X</span><span class="sxs-lookup"><span data-stu-id="156f9-144">X</span></span>|<span data-ttu-id="156f9-145">X</span><span class="sxs-lookup"><span data-stu-id="156f9-145">X</span></span>||||<span data-ttu-id="156f9-146">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="156f9-147">X</span><span class="sxs-lookup"><span data-stu-id="156f9-147">X</span></span>|<span data-ttu-id="156f9-148">X</span><span class="sxs-lookup"><span data-stu-id="156f9-148">X</span></span>||||<span data-ttu-id="156f9-149">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-149">N/A</span></span>|<span data-ttu-id="156f9-150">X</span><span class="sxs-lookup"><span data-stu-id="156f9-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="156f9-151">X</span><span class="sxs-lookup"><span data-stu-id="156f9-151">X</span></span>|<span data-ttu-id="156f9-152">X</span><span class="sxs-lookup"><span data-stu-id="156f9-152">X</span></span>||||<span data-ttu-id="156f9-153">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-153">N/A</span></span>|<span data-ttu-id="156f9-154">X</span><span class="sxs-lookup"><span data-stu-id="156f9-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="156f9-155">X</span><span class="sxs-lookup"><span data-stu-id="156f9-155">X</span></span>|<span data-ttu-id="156f9-156">X</span><span class="sxs-lookup"><span data-stu-id="156f9-156">X</span></span>||<span data-ttu-id="156f9-157">X</span><span class="sxs-lookup"><span data-stu-id="156f9-157">X</span></span>||<span data-ttu-id="156f9-158">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-158">N/A</span></span>|<span data-ttu-id="156f9-159">X</span><span class="sxs-lookup"><span data-stu-id="156f9-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="156f9-160">X</span><span class="sxs-lookup"><span data-stu-id="156f9-160">X</span></span>|<span data-ttu-id="156f9-161">X</span><span class="sxs-lookup"><span data-stu-id="156f9-161">X</span></span>||<span data-ttu-id="156f9-162">X</span><span class="sxs-lookup"><span data-stu-id="156f9-162">X</span></span>|<span data-ttu-id="156f9-163">X</span><span class="sxs-lookup"><span data-stu-id="156f9-163">X</span></span>|<span data-ttu-id="156f9-164">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-164">N/A</span></span>|<span data-ttu-id="156f9-165">X</span><span class="sxs-lookup"><span data-stu-id="156f9-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="156f9-166">X</span><span class="sxs-lookup"><span data-stu-id="156f9-166">X</span></span>|<span data-ttu-id="156f9-167">X</span><span class="sxs-lookup"><span data-stu-id="156f9-167">X</span></span>||<span data-ttu-id="156f9-168">X</span><span class="sxs-lookup"><span data-stu-id="156f9-168">X</span></span>|<span data-ttu-id="156f9-169">X</span><span class="sxs-lookup"><span data-stu-id="156f9-169">X</span></span>|<span data-ttu-id="156f9-170">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-170">N/A</span></span>|<span data-ttu-id="156f9-171">X</span><span class="sxs-lookup"><span data-stu-id="156f9-171">X</span></span>|  
|<span data-ttu-id="156f9-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="156f9-172">eFastExitProcess</span></span>|<span data-ttu-id="156f9-173">X</span><span class="sxs-lookup"><span data-stu-id="156f9-173">X</span></span>|<span data-ttu-id="156f9-174">X</span><span class="sxs-lookup"><span data-stu-id="156f9-174">X</span></span>||<span data-ttu-id="156f9-175">X</span><span class="sxs-lookup"><span data-stu-id="156f9-175">X</span></span>|<span data-ttu-id="156f9-176">X</span><span class="sxs-lookup"><span data-stu-id="156f9-176">X</span></span>|<span data-ttu-id="156f9-177">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="156f9-178">X</span><span class="sxs-lookup"><span data-stu-id="156f9-178">X</span></span>|<span data-ttu-id="156f9-179">X</span><span class="sxs-lookup"><span data-stu-id="156f9-179">X</span></span>|<span data-ttu-id="156f9-180">X</span><span class="sxs-lookup"><span data-stu-id="156f9-180">X</span></span>|<span data-ttu-id="156f9-181">X</span><span class="sxs-lookup"><span data-stu-id="156f9-181">X</span></span>|<span data-ttu-id="156f9-182">X</span><span class="sxs-lookup"><span data-stu-id="156f9-182">X</span></span>|<span data-ttu-id="156f9-183">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="156f9-184">X</span><span class="sxs-lookup"><span data-stu-id="156f9-184">X</span></span>|<span data-ttu-id="156f9-185">X</span><span class="sxs-lookup"><span data-stu-id="156f9-185">X</span></span>|<span data-ttu-id="156f9-186">X</span><span class="sxs-lookup"><span data-stu-id="156f9-186">X</span></span>|<span data-ttu-id="156f9-187">X</span><span class="sxs-lookup"><span data-stu-id="156f9-187">X</span></span>|<span data-ttu-id="156f9-188">X</span><span class="sxs-lookup"><span data-stu-id="156f9-188">X</span></span>|<span data-ttu-id="156f9-189">Není k dispozici</span><span class="sxs-lookup"><span data-stu-id="156f9-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="156f9-190">Požadavky</span><span class="sxs-lookup"><span data-stu-id="156f9-190">Requirements</span></span>  
 <span data-ttu-id="156f9-191">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="156f9-191">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156f9-192">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="156f9-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="156f9-193">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="156f9-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="156f9-194">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156f9-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156f9-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="156f9-195">See also</span></span>

- [<span data-ttu-id="156f9-196">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="156f9-196">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="156f9-197">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="156f9-197">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="156f9-198">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="156f9-198">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="156f9-199">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="156f9-199">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
