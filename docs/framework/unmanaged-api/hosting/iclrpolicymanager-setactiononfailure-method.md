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
ms.openlocfilehash: fb2ecc80f272a3fc9b63b20c5956e7a28f117784
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703471"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="1ef96-102">ICLRPolicyManager::SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="1ef96-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="1ef96-103">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.</span><span class="sxs-lookup"><span data-stu-id="1ef96-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ef96-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ef96-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="1ef96-106">pro Jedna z hodnot [EClrFailure –](eclrfailure-enumeration.md) , která označuje typ selhání, u kterého se má provést akce.</span><span class="sxs-lookup"><span data-stu-id="1ef96-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="1ef96-107">pro Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) označující akci, která se má provést, když dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="1ef96-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="1ef96-108">Seznam podporovaných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="1ef96-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ef96-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1ef96-109">Return Value</span></span>  
  
|<span data-ttu-id="1ef96-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ef96-110">HRESULT</span></span>|<span data-ttu-id="1ef96-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1ef96-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ef96-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ef96-112">S_OK</span></span>|<span data-ttu-id="1ef96-113">`SetActionOnFailure`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1ef96-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="1ef96-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ef96-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ef96-115">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1ef96-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ef96-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ef96-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ef96-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1ef96-117">The call timed out.</span></span>|  
|<span data-ttu-id="1ef96-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ef96-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ef96-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="1ef96-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ef96-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ef96-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ef96-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="1ef96-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ef96-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ef96-122">E_FAIL</span></span>|<span data-ttu-id="1ef96-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="1ef96-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ef96-124">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="1ef96-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ef96-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1ef96-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ef96-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1ef96-126">E_INVALIDARG</span></span>|<span data-ttu-id="1ef96-127">Pro zadanou operaci nelze nastavit akci zásad, nebo byla pro tuto operaci zadána neplatná akce zásad.</span><span class="sxs-lookup"><span data-stu-id="1ef96-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef96-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ef96-128">Remarks</span></span>  
 <span data-ttu-id="1ef96-129">Ve výchozím nastavení vyvolá CLR výjimku, když se nepovede přidělit prostředek, jako je například paměť.</span><span class="sxs-lookup"><span data-stu-id="1ef96-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="1ef96-130">`SetActionOnFailure`umožňuje hostiteli přepsat toto chování zadáním akce zásady, která se má provést při selhání.</span><span class="sxs-lookup"><span data-stu-id="1ef96-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="1ef96-131">V následující tabulce jsou uvedeny kombinace hodnot [EClrFailure –](eclrfailure-enumeration.md) a [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , které jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="1ef96-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="1ef96-132">(Předpona FAIL_ je vynechána z hodnot [EClrFailure –](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="1ef96-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="1ef96-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="1ef96-133">NonCriticalResource</span></span>|<span data-ttu-id="1ef96-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="1ef96-134">CriticalResource</span></span>|<span data-ttu-id="1ef96-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="1ef96-135">FatalRuntime</span></span>|<span data-ttu-id="1ef96-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="1ef96-136">OrphanedLock</span></span>|<span data-ttu-id="1ef96-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="1ef96-137">StackOverflow</span></span>|<span data-ttu-id="1ef96-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="1ef96-138">AccessViolation</span></span>|<span data-ttu-id="1ef96-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="1ef96-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="1ef96-140">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-140">X</span></span>|<span data-ttu-id="1ef96-141">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-141">X</span></span>||||<span data-ttu-id="1ef96-142">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-142">N/A</span></span>||  
|<span data-ttu-id="1ef96-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="1ef96-143">eThrowException</span></span>|<span data-ttu-id="1ef96-144">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-144">X</span></span>|<span data-ttu-id="1ef96-145">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-145">X</span></span>||||<span data-ttu-id="1ef96-146">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="1ef96-147">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-147">X</span></span>|<span data-ttu-id="1ef96-148">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-148">X</span></span>||||<span data-ttu-id="1ef96-149">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-149">N/A</span></span>|<span data-ttu-id="1ef96-150">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="1ef96-151">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-151">X</span></span>|<span data-ttu-id="1ef96-152">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-152">X</span></span>||||<span data-ttu-id="1ef96-153">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-153">N/A</span></span>|<span data-ttu-id="1ef96-154">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="1ef96-155">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-155">X</span></span>|<span data-ttu-id="1ef96-156">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-156">X</span></span>||<span data-ttu-id="1ef96-157">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-157">X</span></span>||<span data-ttu-id="1ef96-158">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-158">N/A</span></span>|<span data-ttu-id="1ef96-159">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="1ef96-160">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-160">X</span></span>|<span data-ttu-id="1ef96-161">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-161">X</span></span>||<span data-ttu-id="1ef96-162">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-162">X</span></span>|<span data-ttu-id="1ef96-163">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-163">X</span></span>|<span data-ttu-id="1ef96-164">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-164">N/A</span></span>|<span data-ttu-id="1ef96-165">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="1ef96-166">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-166">X</span></span>|<span data-ttu-id="1ef96-167">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-167">X</span></span>||<span data-ttu-id="1ef96-168">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-168">X</span></span>|<span data-ttu-id="1ef96-169">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-169">X</span></span>|<span data-ttu-id="1ef96-170">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-170">N/A</span></span>|<span data-ttu-id="1ef96-171">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-171">X</span></span>|  
|<span data-ttu-id="1ef96-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="1ef96-172">eFastExitProcess</span></span>|<span data-ttu-id="1ef96-173">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-173">X</span></span>|<span data-ttu-id="1ef96-174">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-174">X</span></span>||<span data-ttu-id="1ef96-175">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-175">X</span></span>|<span data-ttu-id="1ef96-176">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-176">X</span></span>|<span data-ttu-id="1ef96-177">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="1ef96-178">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-178">X</span></span>|<span data-ttu-id="1ef96-179">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-179">X</span></span>|<span data-ttu-id="1ef96-180">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-180">X</span></span>|<span data-ttu-id="1ef96-181">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-181">X</span></span>|<span data-ttu-id="1ef96-182">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-182">X</span></span>|<span data-ttu-id="1ef96-183">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="1ef96-184">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-184">X</span></span>|<span data-ttu-id="1ef96-185">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-185">X</span></span>|<span data-ttu-id="1ef96-186">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-186">X</span></span>|<span data-ttu-id="1ef96-187">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-187">X</span></span>|<span data-ttu-id="1ef96-188">×</span><span class="sxs-lookup"><span data-stu-id="1ef96-188">X</span></span>|<span data-ttu-id="1ef96-189">–</span><span class="sxs-lookup"><span data-stu-id="1ef96-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="1ef96-190">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ef96-190">Requirements</span></span>  
 <span data-ttu-id="1ef96-191">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef96-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef96-192">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ef96-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ef96-193">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ef96-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ef96-194">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef96-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef96-195">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ef96-195">See also</span></span>

- [<span data-ttu-id="1ef96-196">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="1ef96-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="1ef96-197">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="1ef96-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="1ef96-198">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ef96-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1ef96-199">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ef96-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
