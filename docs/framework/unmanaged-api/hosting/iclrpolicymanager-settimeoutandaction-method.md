---
title: "ICLRPolicyManager::SetTimeoutAndAction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeoutAndAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67150b7544f1d8d25532c564800404b634cae99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="d9030-102">ICLRPolicyManager::SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="d9030-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="d9030-103">Nastaví hodnotu časového limitu pro zadanou operaci a určuje zásad akci, kterou common language runtime (CLR) má provést, když dojde k operaci.</span><span class="sxs-lookup"><span data-stu-id="d9030-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9030-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9030-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9030-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9030-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="d9030-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje operaci, pro kterou chcete nastavit časový limit a zásady `action`.</span><span class="sxs-lookup"><span data-stu-id="d9030-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="d9030-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d9030-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d9030-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="d9030-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="d9030-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="d9030-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="d9030-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d9030-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="d9030-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d9030-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="d9030-112">[v] Nová hodnota časového limitu, v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="d9030-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="d9030-113">Hodnota NEKONEČNÉ příčiny `operation` nikdy k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="d9030-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="d9030-114">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci zásady, kterou modulu CLR by měla provést v případě `operation` dojde.</span><span class="sxs-lookup"><span data-stu-id="d9030-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9030-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d9030-115">Return Value</span></span>  
  
|<span data-ttu-id="d9030-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9030-116">HRESULT</span></span>|<span data-ttu-id="d9030-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d9030-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9030-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9030-118">S_OK</span></span>|<span data-ttu-id="d9030-119">`SetTimeoutAndAction`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d9030-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="d9030-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9030-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9030-121">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d9030-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9030-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9030-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9030-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d9030-123">The call timed out.</span></span>|  
|<span data-ttu-id="d9030-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9030-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9030-125">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d9030-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9030-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9030-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9030-127">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d9030-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9030-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9030-128">E_FAIL</span></span>|<span data-ttu-id="d9030-129">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d9030-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9030-130">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d9030-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9030-131">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d9030-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9030-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d9030-132">E_INVALIDARG</span></span>|<span data-ttu-id="d9030-133">Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `action`.</span><span class="sxs-lookup"><span data-stu-id="d9030-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9030-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9030-134">Remarks</span></span>  
 <span data-ttu-id="d9030-135">`SetTimeoutAndAction`zapouzdřuje funkce [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) a [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody a může být volána místo sekvenční volání na tyto dvě metody.</span><span class="sxs-lookup"><span data-stu-id="d9030-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d9030-136">Ne všechny akce hodnoty zásad lze zadat jako chování vypršení časového limitu pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="d9030-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="d9030-137">Najdete v částech poznámky témat pro tyto dvě metody platné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d9030-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9030-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9030-138">Requirements</span></span>  
 <span data-ttu-id="d9030-139">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9030-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9030-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9030-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9030-141">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9030-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9030-142">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9030-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9030-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9030-143">See Also</span></span>  
 [<span data-ttu-id="d9030-144">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="d9030-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="d9030-145">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="d9030-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="d9030-146">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9030-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="d9030-147">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="d9030-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [<span data-ttu-id="d9030-148">Iclrpolicymanager::settimeoutandaction –</span><span class="sxs-lookup"><span data-stu-id="d9030-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
