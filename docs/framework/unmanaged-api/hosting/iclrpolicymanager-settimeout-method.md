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
ms.openlocfilehash: b16cc6a899b1ad5c814c29a93c6125250ca8186d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133572"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="58306-102">ICLRPolicyManager::SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="58306-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="58306-103">Nastaví hodnotu časového limitu pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="58306-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58306-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58306-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58306-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58306-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="58306-106">[in] Jeden z [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty určující běžné operace jazyka runtime (CLR) pro kterou chcete nastavit vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="58306-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="58306-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="58306-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="58306-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="58306-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="58306-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="58306-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="58306-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="58306-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="58306-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="58306-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="58306-112">[in] Nová hodnota časového limitu, v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="58306-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="58306-113">Hodnota NEKONEČNO způsobí, že nikdy na vypršení časového limitu operace.</span><span class="sxs-lookup"><span data-stu-id="58306-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58306-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="58306-114">Return Value</span></span>  
  
|<span data-ttu-id="58306-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58306-115">HRESULT</span></span>|<span data-ttu-id="58306-116">Popis</span><span class="sxs-lookup"><span data-stu-id="58306-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58306-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="58306-117">S_OK</span></span>|<span data-ttu-id="58306-118">`SetTimeout` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="58306-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="58306-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58306-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58306-120">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="58306-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58306-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58306-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58306-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="58306-122">The call timed out.</span></span>|  
|<span data-ttu-id="58306-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58306-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58306-124">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="58306-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58306-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58306-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58306-126">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="58306-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58306-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58306-127">E_FAIL</span></span>|<span data-ttu-id="58306-128">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="58306-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58306-129">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="58306-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58306-130">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="58306-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="58306-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="58306-131">E_INVALIDARG</span></span>|<span data-ttu-id="58306-132">Nelze nastavit vypršení časového limitu pro zadaný rozbočovač `operation`, nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="58306-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58306-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58306-133">Requirements</span></span>  
 <span data-ttu-id="58306-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58306-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58306-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58306-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58306-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58306-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58306-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58306-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58306-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58306-138">See also</span></span>

- [<span data-ttu-id="58306-139">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="58306-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="58306-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58306-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="58306-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58306-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
