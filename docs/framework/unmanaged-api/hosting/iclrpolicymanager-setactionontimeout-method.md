---
title: "ICLRPolicyManager::SetActionOnTimeout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetActionOnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db0918272a315e78191624cbe6420863285620c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="92b3b-102">ICLRPolicyManager::SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="92b3b-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="92b3b-103">Určuje akci zásady, které modul CLR (CLR) má provést, pokud zadaná operace vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="92b3b-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92b3b-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92b3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92b3b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="92b3b-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje operaci, pro který chcete zadat časový limit akce.</span><span class="sxs-lookup"><span data-stu-id="92b3b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="92b3b-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="92b3b-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="92b3b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="92b3b-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="92b3b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="92b3b-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="92b3b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92b3b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="92b3b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92b3b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="92b3b-112">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci zásady mají být provedeny, když vyprší časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="92b3b-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92b3b-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="92b3b-113">Return Value</span></span>  
  
|<span data-ttu-id="92b3b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92b3b-114">HRESULT</span></span>|<span data-ttu-id="92b3b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="92b3b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92b3b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="92b3b-116">S_OK</span></span>|<span data-ttu-id="92b3b-117">`SetActionOnTimeout`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="92b3b-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="92b3b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92b3b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92b3b-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="92b3b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92b3b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92b3b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92b3b-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="92b3b-121">The call timed out.</span></span>|  
|<span data-ttu-id="92b3b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92b3b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92b3b-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="92b3b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92b3b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92b3b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92b3b-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="92b3b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92b3b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92b3b-126">E_FAIL</span></span>|<span data-ttu-id="92b3b-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="92b3b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92b3b-128">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="92b3b-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92b3b-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="92b3b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92b3b-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="92b3b-130">E_INVALIDARG</span></span>|<span data-ttu-id="92b3b-131">Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="92b3b-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92b3b-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92b3b-132">Remarks</span></span>  
 <span data-ttu-id="92b3b-133">Hodnota časového limitu může být buď výchozí časový limit stanovené CLR, nebo má hodnotu pro hostitele v volání [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="92b3b-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="92b3b-134">Ne všechny akce hodnoty zásad lze zadat jako chování vypršení časového limitu pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="92b3b-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="92b3b-135">`SetActionOnTimeout`Obvykle se používá pouze pro zvýšení chování.</span><span class="sxs-lookup"><span data-stu-id="92b3b-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="92b3b-136">Například hostitel můžete určit, že vlákno přerušení být převedena na článku neslušní vláken přerušení, ale nelze zadat jako opak.</span><span class="sxs-lookup"><span data-stu-id="92b3b-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="92b3b-137">Následující tabulka popisuje platném `action` hodnoty platný `operation` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="92b3b-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="92b3b-138">Hodnota pro`operation`</span><span class="sxs-lookup"><span data-stu-id="92b3b-138">Value for `operation`</span></span>|<span data-ttu-id="92b3b-139">Platné hodnoty pro`action`</span><span class="sxs-lookup"><span data-stu-id="92b3b-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="92b3b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92b3b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="92b3b-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="92b3b-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="92b3b-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="92b3b-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="92b3b-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="92b3b-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="92b3b-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="92b3b-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="92b3b-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-145">-   eExitProcess</span></span><br /><span data-ttu-id="92b3b-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="92b3b-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="92b3b-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="92b3b-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="92b3b-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="92b3b-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="92b3b-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="92b3b-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="92b3b-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="92b3b-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="92b3b-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-152">-   eExitProcess</span></span><br /><span data-ttu-id="92b3b-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="92b3b-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="92b3b-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="92b3b-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="92b3b-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="92b3b-156">OPR_ProcessExit</span></span>|<span data-ttu-id="92b3b-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-157">-   eExitProcess</span></span><br /><span data-ttu-id="92b3b-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="92b3b-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="92b3b-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="92b3b-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="92b3b-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92b3b-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92b3b-161">Requirements</span></span>  
 <span data-ttu-id="92b3b-162">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b3b-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b3b-163">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92b3b-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92b3b-164">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92b3b-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92b3b-165">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b3b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b3b-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="92b3b-166">See Also</span></span>  
 [<span data-ttu-id="92b3b-167">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="92b3b-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="92b3b-168">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="92b3b-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="92b3b-169">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92b3b-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="92b3b-170">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92b3b-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
