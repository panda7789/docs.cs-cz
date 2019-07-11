---
title: ICLRPolicyManager::SetTimeoutAndAction – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c58c14dbc11272a40de01140db72ac3605bfbc67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757256"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="d7963-102">ICLRPolicyManager::SetTimeoutAndAction – metoda</span><span class="sxs-lookup"><span data-stu-id="d7963-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="d7963-103">Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad by měl trvat common language runtime (CLR), když dojde k operaci.</span><span class="sxs-lookup"><span data-stu-id="d7963-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7963-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7963-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7963-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="d7963-106">[in] Jeden z [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty určující operace, pro kterou chcete nastavit časový limit a zásady `action`.</span><span class="sxs-lookup"><span data-stu-id="d7963-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="d7963-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d7963-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="d7963-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="d7963-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="d7963-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="d7963-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="d7963-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d7963-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="d7963-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="d7963-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="d7963-112">[in] Nová hodnota časového limitu, v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="d7963-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="d7963-113">Hodnota NEKONEČNÉ příčiny `operation` nikdy k vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="d7963-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="d7963-114">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty označující, že modul CLR by měla provést v případě akce zásad `operation` vyvolá.</span><span class="sxs-lookup"><span data-stu-id="d7963-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7963-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d7963-115">Return Value</span></span>  
  
|<span data-ttu-id="d7963-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7963-116">HRESULT</span></span>|<span data-ttu-id="d7963-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d7963-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7963-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7963-118">S_OK</span></span>|<span data-ttu-id="d7963-119">`SetTimeoutAndAction` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d7963-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="d7963-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7963-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7963-121">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d7963-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7963-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7963-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7963-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d7963-123">The call timed out.</span></span>|  
|<span data-ttu-id="d7963-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7963-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7963-125">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d7963-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7963-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7963-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7963-127">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d7963-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7963-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7963-128">E_FAIL</span></span>|<span data-ttu-id="d7963-129">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d7963-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7963-130">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d7963-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7963-131">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d7963-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d7963-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d7963-132">E_INVALIDARG</span></span>|<span data-ttu-id="d7963-133">Nelze nastavit vypršení časového limitu pro zadaný rozbočovač `operation`, nebo byla zadána neplatná hodnota pro `action`.</span><span class="sxs-lookup"><span data-stu-id="d7963-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7963-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7963-134">Remarks</span></span>  
 <span data-ttu-id="d7963-135">`SetTimeoutAndAction` zapouzdřuje funkce [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) a [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody a může být volána místo sekvenční volání těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="d7963-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7963-136">Ne všechny akce hodnoty zásad se dá nastavit jako chování časový limit pro operace CLR.</span><span class="sxs-lookup"><span data-stu-id="d7963-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="d7963-137">Najdete v části poznámky v tématech pro tyto dvě metody pro platné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d7963-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7963-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7963-138">Requirements</span></span>  
 <span data-ttu-id="d7963-139">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7963-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7963-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7963-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7963-141">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7963-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7963-142">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7963-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7963-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7963-143">See also</span></span>

- [<span data-ttu-id="d7963-144">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="d7963-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="d7963-145">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="d7963-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d7963-146">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7963-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d7963-147">SetActionOnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="d7963-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="d7963-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="d7963-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
