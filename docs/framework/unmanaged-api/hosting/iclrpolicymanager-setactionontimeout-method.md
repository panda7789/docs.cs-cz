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
ms.openlocfilehash: 924a8a64fb698ec0e78397ad791f445297c0fee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="09076-102">ICLRPolicyManager::SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="09076-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="09076-103">Určuje akci zásady, které modul CLR (CLR) má provést, pokud zadaná operace vyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="09076-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09076-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09076-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09076-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09076-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="09076-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje operaci, pro který chcete zadat časový limit akce.</span><span class="sxs-lookup"><span data-stu-id="09076-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="09076-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="09076-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="09076-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="09076-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="09076-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="09076-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="09076-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="09076-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="09076-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="09076-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="09076-112">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci zásady mají být provedeny, když vyprší časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="09076-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09076-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09076-113">Return Value</span></span>  
  
|<span data-ttu-id="09076-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09076-114">HRESULT</span></span>|<span data-ttu-id="09076-115">Popis</span><span class="sxs-lookup"><span data-stu-id="09076-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09076-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="09076-116">S_OK</span></span>|<span data-ttu-id="09076-117">`SetActionOnTimeout`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="09076-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="09076-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09076-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09076-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="09076-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09076-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09076-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09076-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="09076-121">The call timed out.</span></span>|  
|<span data-ttu-id="09076-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09076-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09076-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="09076-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09076-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09076-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09076-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="09076-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09076-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09076-126">E_FAIL</span></span>|<span data-ttu-id="09076-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="09076-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09076-128">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="09076-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09076-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09076-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09076-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="09076-130">E_INVALIDARG</span></span>|<span data-ttu-id="09076-131">Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="09076-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09076-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09076-132">Remarks</span></span>  
 <span data-ttu-id="09076-133">Hodnota časového limitu může být buď výchozí časový limit stanovené CLR, nebo má hodnotu pro hostitele v volání [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="09076-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="09076-134">Ne všechny akce hodnoty zásad lze zadat jako chování vypršení časového limitu pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="09076-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="09076-135">`SetActionOnTimeout`Obvykle se používá pouze pro zvýšení chování.</span><span class="sxs-lookup"><span data-stu-id="09076-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="09076-136">Například hostitel můžete určit, že vlákno přerušení být převedena na článku neslušní vláken přerušení, ale nelze zadat jako opak.</span><span class="sxs-lookup"><span data-stu-id="09076-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="09076-137">Následující tabulka popisuje platném `action` hodnoty platný `operation` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09076-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="09076-138">Hodnota pro`operation`</span><span class="sxs-lookup"><span data-stu-id="09076-138">Value for `operation`</span></span>|<span data-ttu-id="09076-139">Platné hodnoty pro`action`</span><span class="sxs-lookup"><span data-stu-id="09076-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="09076-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="09076-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="09076-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="09076-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="09076-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="09076-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="09076-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="09076-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="09076-144">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="09076-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="09076-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-145">-   eExitProcess</span></span><br /><span data-ttu-id="09076-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="09076-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="09076-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="09076-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="09076-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="09076-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="09076-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="09076-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="09076-151">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="09076-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="09076-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-152">-   eExitProcess</span></span><br /><span data-ttu-id="09076-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="09076-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="09076-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="09076-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="09076-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="09076-156">OPR_ProcessExit</span></span>|<span data-ttu-id="09076-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-157">-   eExitProcess</span></span><br /><span data-ttu-id="09076-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="09076-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="09076-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="09076-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="09076-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09076-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09076-161">Requirements</span></span>  
 <span data-ttu-id="09076-162">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09076-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09076-163">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09076-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09076-164">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09076-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09076-165">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09076-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09076-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="09076-166">See Also</span></span>  
 [<span data-ttu-id="09076-167">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="09076-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="09076-168">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="09076-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="09076-169">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09076-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="09076-170">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09076-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
