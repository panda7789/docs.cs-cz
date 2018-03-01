---
title: "ICLRPolicyManager::SetTimeout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b5042d2f06d25b2cccc81239367362313210d3c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="dd937-102">ICLRPolicyManager::SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="dd937-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="dd937-103">Nastaví hodnotu časového limitu pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="dd937-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd937-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd937-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd937-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd937-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="dd937-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje běžné operace language runtime (CLR) pro kterou chcete nastavit vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="dd937-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="dd937-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="dd937-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="dd937-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="dd937-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="dd937-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="dd937-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="dd937-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="dd937-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="dd937-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="dd937-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="dd937-112">[v] Nová hodnota časového limitu, v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="dd937-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="dd937-113">Hodnota NEKONEČNÉ způsobí, že se nikdy časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="dd937-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd937-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd937-114">Return Value</span></span>  
  
|<span data-ttu-id="dd937-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd937-115">HRESULT</span></span>|<span data-ttu-id="dd937-116">Popis</span><span class="sxs-lookup"><span data-stu-id="dd937-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd937-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd937-117">S_OK</span></span>|<span data-ttu-id="dd937-118">`SetTimeout`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dd937-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="dd937-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd937-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd937-120">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dd937-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd937-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd937-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd937-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dd937-122">The call timed out.</span></span>|  
|<span data-ttu-id="dd937-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd937-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd937-124">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="dd937-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd937-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd937-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd937-126">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="dd937-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd937-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd937-127">E_FAIL</span></span>|<span data-ttu-id="dd937-128">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="dd937-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd937-129">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dd937-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd937-130">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd937-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dd937-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dd937-131">E_INVALIDARG</span></span>|<span data-ttu-id="dd937-132">Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="dd937-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd937-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd937-133">Requirements</span></span>  
 <span data-ttu-id="dd937-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd937-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd937-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dd937-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd937-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd937-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd937-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd937-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd937-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd937-138">See Also</span></span>  
 [<span data-ttu-id="dd937-139">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="dd937-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="dd937-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd937-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="dd937-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd937-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
