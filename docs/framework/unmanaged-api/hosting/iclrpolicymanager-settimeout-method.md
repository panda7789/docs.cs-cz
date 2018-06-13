---
title: ICLRPolicyManager::SetTimeout – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b5a389af718322d1e0fffebae046bf28731877b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435774"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="3e493-102">ICLRPolicyManager::SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="3e493-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="3e493-103">Nastaví hodnotu časového limitu pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="3e493-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e493-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e493-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e493-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e493-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="3e493-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje běžné operace language runtime (CLR) pro kterou chcete nastavit vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="3e493-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="3e493-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="3e493-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="3e493-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3e493-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="3e493-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3e493-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="3e493-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e493-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="3e493-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3e493-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="3e493-112">[v] Nová hodnota časového limitu, v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="3e493-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="3e493-113">Hodnota NEKONEČNÉ způsobí, že se nikdy časový limit operace.</span><span class="sxs-lookup"><span data-stu-id="3e493-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e493-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3e493-114">Return Value</span></span>  
  
|<span data-ttu-id="3e493-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e493-115">HRESULT</span></span>|<span data-ttu-id="3e493-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3e493-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e493-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e493-117">S_OK</span></span>|<span data-ttu-id="3e493-118">`SetTimeout` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3e493-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="3e493-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e493-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e493-120">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3e493-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e493-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e493-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e493-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3e493-122">The call timed out.</span></span>|  
|<span data-ttu-id="3e493-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e493-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e493-124">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="3e493-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e493-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e493-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e493-126">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="3e493-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e493-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e493-127">E_FAIL</span></span>|<span data-ttu-id="3e493-128">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3e493-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e493-129">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3e493-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e493-130">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e493-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e493-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3e493-131">E_INVALIDARG</span></span>|<span data-ttu-id="3e493-132">Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="3e493-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e493-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e493-133">Requirements</span></span>  
 <span data-ttu-id="3e493-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e493-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e493-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e493-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e493-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e493-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e493-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e493-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e493-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e493-138">See Also</span></span>  
 [<span data-ttu-id="3e493-139">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="3e493-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="3e493-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e493-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3e493-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e493-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
