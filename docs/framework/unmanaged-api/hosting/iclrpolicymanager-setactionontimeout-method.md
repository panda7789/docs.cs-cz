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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d99f4f0615e7d25991b37030b7cb609985192f
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910669"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="1932b-102">ICLRPolicyManager::SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="1932b-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>
<span data-ttu-id="1932b-103">Určuje akci zásad by měl trvat common language runtime (CLR), když vyprší časový limit zadaný operace.</span><span class="sxs-lookup"><span data-stu-id="1932b-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1932b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1932b-104">Syntax</span></span>  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1932b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1932b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="1932b-106">[in] Jeden z [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která operaci, pro který chcete zadat časový limit akce.</span><span class="sxs-lookup"><span data-stu-id="1932b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="1932b-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="1932b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="1932b-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="1932b-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="1932b-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="1932b-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="1932b-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1932b-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="1932b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1932b-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="1932b-112">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, která mají být provedeny, když vyprší časový limit operace akce zásad.</span><span class="sxs-lookup"><span data-stu-id="1932b-112">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1932b-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1932b-113">Return Value</span></span>  
  
|<span data-ttu-id="1932b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1932b-114">HRESULT</span></span>|<span data-ttu-id="1932b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1932b-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1932b-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1932b-116">S_OK</span></span>|<span data-ttu-id="1932b-117">`SetActionOnTimeout` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1932b-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="1932b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1932b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1932b-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1932b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1932b-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1932b-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1932b-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1932b-121">The call timed out.</span></span>|  
|<span data-ttu-id="1932b-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1932b-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1932b-123">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="1932b-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1932b-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1932b-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1932b-125">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="1932b-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1932b-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1932b-126">E_FAIL</span></span>|<span data-ttu-id="1932b-127">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1932b-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1932b-128">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1932b-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1932b-129">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1932b-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1932b-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1932b-130">E_INVALIDARG</span></span>|<span data-ttu-id="1932b-131">Nelze nastavit vypršení časového limitu pro zadaný rozbočovač `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="1932b-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1932b-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1932b-132">Remarks</span></span>  
 <span data-ttu-id="1932b-133">Hodnota časového limitu může být buď výchozí časový limit nastavený platformou CLR, nebo hodnotu zadanou pomocí hostitele ve volání [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1932b-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="1932b-134">Ne všechny akce hodnoty zásad se dá nastavit jako chování časový limit pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="1932b-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="1932b-135">`SetActionOnTimeout` Obvykle se používá pouze ke zvýšení úrovně chování.</span><span class="sxs-lookup"><span data-stu-id="1932b-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="1932b-136">Například hostitele můžete určit, že vlákno přeruší převeden na článku neslušní vlákna přerušení, ale nelze zadat opak.</span><span class="sxs-lookup"><span data-stu-id="1932b-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="1932b-137">Následující tabulka popisuje platnými `action` hodnoty platné `operation` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1932b-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="1932b-138">Hodnota pro `operation`</span><span class="sxs-lookup"><span data-stu-id="1932b-138">Value for `operation`</span></span>|<span data-ttu-id="1932b-139">Platné hodnoty pro `action`</span><span class="sxs-lookup"><span data-stu-id="1932b-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="1932b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1932b-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="1932b-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1932b-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="1932b-142">-   eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="1932b-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="1932b-143">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="1932b-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="1932b-144">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="1932b-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="1932b-145">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-145">-   eExitProcess</span></span><br /><span data-ttu-id="1932b-146">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="1932b-147">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="1932b-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="1932b-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="1932b-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="1932b-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="1932b-150">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="1932b-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="1932b-151">-   eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="1932b-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="1932b-152">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-152">-   eExitProcess</span></span><br /><span data-ttu-id="1932b-153">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="1932b-154">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="1932b-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="1932b-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="1932b-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="1932b-156">OPR_ProcessExit</span></span>|<span data-ttu-id="1932b-157">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-157">-   eExitProcess</span></span><br /><span data-ttu-id="1932b-158">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="1932b-159">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="1932b-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="1932b-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="1932b-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1932b-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1932b-161">Requirements</span></span>  
 <span data-ttu-id="1932b-162">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1932b-162">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1932b-163">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1932b-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1932b-164">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1932b-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1932b-165">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1932b-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1932b-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1932b-166">See also</span></span>

- [<span data-ttu-id="1932b-167">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="1932b-167">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="1932b-168">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="1932b-168">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="1932b-169">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1932b-169">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1932b-170">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1932b-170">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
