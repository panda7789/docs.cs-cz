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
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504105"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="b37a2-102">ICLRPolicyManager::SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="b37a2-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="b37a2-103">Určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu zadaného selhání.</span><span class="sxs-lookup"><span data-stu-id="b37a2-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b37a2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b37a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b37a2-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="b37a2-106">pro Jedna z hodnot [EClrFailure –](eclrfailure-enumeration.md) , která označuje typ selhání, u kterého se má provést akce.</span><span class="sxs-lookup"><span data-stu-id="b37a2-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="b37a2-107">pro Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) označující akci, která se má provést, když dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="b37a2-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="b37a2-108">Seznam podporovaných hodnot naleznete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="b37a2-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b37a2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b37a2-109">Return Value</span></span>  
  
|<span data-ttu-id="b37a2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b37a2-110">HRESULT</span></span>|<span data-ttu-id="b37a2-111">Description</span><span class="sxs-lookup"><span data-stu-id="b37a2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b37a2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b37a2-112">S_OK</span></span>|<span data-ttu-id="b37a2-113">`SetActionOnFailure`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b37a2-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="b37a2-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b37a2-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b37a2-115">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b37a2-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b37a2-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b37a2-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b37a2-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b37a2-117">The call timed out.</span></span>|  
|<span data-ttu-id="b37a2-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b37a2-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b37a2-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b37a2-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b37a2-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b37a2-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b37a2-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b37a2-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b37a2-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b37a2-122">E_FAIL</span></span>|<span data-ttu-id="b37a2-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b37a2-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b37a2-124">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="b37a2-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b37a2-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b37a2-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b37a2-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b37a2-126">E_INVALIDARG</span></span>|<span data-ttu-id="b37a2-127">Pro zadanou operaci nelze nastavit akci zásad, nebo byla pro tuto operaci zadána neplatná akce zásad.</span><span class="sxs-lookup"><span data-stu-id="b37a2-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b37a2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b37a2-128">Remarks</span></span>  
 <span data-ttu-id="b37a2-129">Ve výchozím nastavení vyvolá CLR výjimku, když se nepovede přidělit prostředek, jako je například paměť.</span><span class="sxs-lookup"><span data-stu-id="b37a2-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="b37a2-130">`SetActionOnFailure`umožňuje hostiteli přepsat toto chování zadáním akce zásady, která se má provést při selhání.</span><span class="sxs-lookup"><span data-stu-id="b37a2-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="b37a2-131">V následující tabulce jsou uvedeny kombinace hodnot [EClrFailure –](eclrfailure-enumeration.md) a [EPolicyAction –](epolicyaction-enumeration.md) , které jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="b37a2-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="b37a2-132">(Předpona FAIL_ je vynechána z hodnot [EClrFailure –](eclrfailure-enumeration.md) .)</span><span class="sxs-lookup"><span data-stu-id="b37a2-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="b37a2-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="b37a2-133">NonCriticalResource</span></span>|<span data-ttu-id="b37a2-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="b37a2-134">CriticalResource</span></span>|<span data-ttu-id="b37a2-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="b37a2-135">FatalRuntime</span></span>|<span data-ttu-id="b37a2-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="b37a2-136">OrphanedLock</span></span>|<span data-ttu-id="b37a2-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="b37a2-137">StackOverflow</span></span>|<span data-ttu-id="b37a2-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="b37a2-138">AccessViolation</span></span>|<span data-ttu-id="b37a2-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="b37a2-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="b37a2-140">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-140">X</span></span>|<span data-ttu-id="b37a2-141">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-141">X</span></span>||||<span data-ttu-id="b37a2-142">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-142">N/A</span></span>||  
|<span data-ttu-id="b37a2-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="b37a2-143">eThrowException</span></span>|<span data-ttu-id="b37a2-144">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-144">X</span></span>|<span data-ttu-id="b37a2-145">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-145">X</span></span>||||<span data-ttu-id="b37a2-146">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="b37a2-147">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-147">X</span></span>|<span data-ttu-id="b37a2-148">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-148">X</span></span>||||<span data-ttu-id="b37a2-149">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-149">N/A</span></span>|<span data-ttu-id="b37a2-150">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b37a2-151">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-151">X</span></span>|<span data-ttu-id="b37a2-152">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-152">X</span></span>||||<span data-ttu-id="b37a2-153">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-153">N/A</span></span>|<span data-ttu-id="b37a2-154">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b37a2-155">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-155">X</span></span>|<span data-ttu-id="b37a2-156">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-156">X</span></span>||<span data-ttu-id="b37a2-157">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-157">X</span></span>||<span data-ttu-id="b37a2-158">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-158">N/A</span></span>|<span data-ttu-id="b37a2-159">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b37a2-160">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-160">X</span></span>|<span data-ttu-id="b37a2-161">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-161">X</span></span>||<span data-ttu-id="b37a2-162">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-162">X</span></span>|<span data-ttu-id="b37a2-163">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-163">X</span></span>|<span data-ttu-id="b37a2-164">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-164">N/A</span></span>|<span data-ttu-id="b37a2-165">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="b37a2-166">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-166">X</span></span>|<span data-ttu-id="b37a2-167">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-167">X</span></span>||<span data-ttu-id="b37a2-168">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-168">X</span></span>|<span data-ttu-id="b37a2-169">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-169">X</span></span>|<span data-ttu-id="b37a2-170">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-170">N/A</span></span>|<span data-ttu-id="b37a2-171">×</span><span class="sxs-lookup"><span data-stu-id="b37a2-171">X</span></span>|  
|<span data-ttu-id="b37a2-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="b37a2-172">eFastExitProcess</span></span>|<span data-ttu-id="b37a2-173">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-173">X</span></span>|<span data-ttu-id="b37a2-174">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-174">X</span></span>||<span data-ttu-id="b37a2-175">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-175">X</span></span>|<span data-ttu-id="b37a2-176">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-176">X</span></span>|<span data-ttu-id="b37a2-177">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="b37a2-178">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-178">X</span></span>|<span data-ttu-id="b37a2-179">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-179">X</span></span>|<span data-ttu-id="b37a2-180">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-180">X</span></span>|<span data-ttu-id="b37a2-181">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-181">X</span></span>|<span data-ttu-id="b37a2-182">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-182">X</span></span>|<span data-ttu-id="b37a2-183">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="b37a2-184">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-184">X</span></span>|<span data-ttu-id="b37a2-185">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-185">X</span></span>|<span data-ttu-id="b37a2-186">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-186">X</span></span>|<span data-ttu-id="b37a2-187">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-187">X</span></span>|<span data-ttu-id="b37a2-188">X</span><span class="sxs-lookup"><span data-stu-id="b37a2-188">X</span></span>|<span data-ttu-id="b37a2-189">–</span><span class="sxs-lookup"><span data-stu-id="b37a2-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="b37a2-190">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b37a2-190">Requirements</span></span>  
 <span data-ttu-id="b37a2-191">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b37a2-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37a2-192">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b37a2-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b37a2-193">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b37a2-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b37a2-194">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37a2-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37a2-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b37a2-195">See also</span></span>

- [<span data-ttu-id="b37a2-196">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="b37a2-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="b37a2-197">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="b37a2-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b37a2-198">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b37a2-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="b37a2-199">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b37a2-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
