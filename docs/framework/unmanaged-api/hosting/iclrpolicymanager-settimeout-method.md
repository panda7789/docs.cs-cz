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
ms.openlocfilehash: 516ba1325404e757af8e38de239864b21b1640f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140756"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="370a6-102">ICLRPolicyManager::SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="370a6-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="370a6-103">Nastaví hodnotu časového limitu pro zadanou operaci.</span><span class="sxs-lookup"><span data-stu-id="370a6-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="370a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="370a6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="370a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="370a6-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="370a6-106">pro Jedna z hodnot [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , která označuje operaci modulu CLR (Common Language Runtime), pro kterou chcete nastavit časový limit.</span><span class="sxs-lookup"><span data-stu-id="370a6-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="370a6-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="370a6-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="370a6-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="370a6-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="370a6-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="370a6-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="370a6-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="370a6-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="370a6-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="370a6-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="370a6-112">pro Nová hodnota časového limitu v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="370a6-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="370a6-113">Hodnota nekonečno způsobí, že operace nikdy nevyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="370a6-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="370a6-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="370a6-114">Return Value</span></span>  
  
|<span data-ttu-id="370a6-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="370a6-115">HRESULT</span></span>|<span data-ttu-id="370a6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="370a6-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="370a6-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="370a6-117">S_OK</span></span>|<span data-ttu-id="370a6-118">`SetTimeout` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="370a6-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="370a6-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="370a6-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="370a6-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="370a6-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="370a6-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="370a6-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="370a6-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="370a6-122">The call timed out.</span></span>|  
|<span data-ttu-id="370a6-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="370a6-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="370a6-124">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="370a6-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="370a6-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="370a6-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="370a6-126">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="370a6-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="370a6-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="370a6-127">E_FAIL</span></span>|<span data-ttu-id="370a6-128">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="370a6-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="370a6-129">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="370a6-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="370a6-130">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="370a6-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="370a6-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="370a6-131">E_INVALIDARG</span></span>|<span data-ttu-id="370a6-132">Pro zadaný `operation`nelze nastavit časový limit nebo byla zadána neplatná hodnota pro `operation`.</span><span class="sxs-lookup"><span data-stu-id="370a6-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="370a6-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="370a6-133">Requirements</span></span>  
 <span data-ttu-id="370a6-134">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="370a6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="370a6-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="370a6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="370a6-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="370a6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="370a6-137">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="370a6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370a6-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="370a6-138">See also</span></span>

- [<span data-ttu-id="370a6-139">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="370a6-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="370a6-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="370a6-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="370a6-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="370a6-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
