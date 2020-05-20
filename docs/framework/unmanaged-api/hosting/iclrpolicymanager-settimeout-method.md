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
ms.openlocfilehash: b3e66a1e04ca3f3031adf1f0f7f71d689ee76b04
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703419"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="851cf-102">ICLRPolicyManager::SetTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="851cf-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="851cf-103">Nastaví hodnotu časového limitu pro zadanou operaci.</span><span class="sxs-lookup"><span data-stu-id="851cf-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="851cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="851cf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="851cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="851cf-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="851cf-106">pro Jedna z hodnot [EClrOperation –](eclroperation-enumeration.md) , která označuje operaci modulu CLR (Common Language Runtime), pro kterou chcete nastavit časový limit.</span><span class="sxs-lookup"><span data-stu-id="851cf-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="851cf-107">Podporovány jsou následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="851cf-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="851cf-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="851cf-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="851cf-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="851cf-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="851cf-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="851cf-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="851cf-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="851cf-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="851cf-112">pro Nová hodnota časového limitu v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="851cf-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="851cf-113">Hodnota nekonečno způsobí, že operace nikdy nevyprší časový limit.</span><span class="sxs-lookup"><span data-stu-id="851cf-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="851cf-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="851cf-114">Return Value</span></span>  
  
|<span data-ttu-id="851cf-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="851cf-115">HRESULT</span></span>|<span data-ttu-id="851cf-116">Popis</span><span class="sxs-lookup"><span data-stu-id="851cf-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="851cf-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="851cf-117">S_OK</span></span>|<span data-ttu-id="851cf-118">`SetTimeout`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="851cf-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="851cf-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="851cf-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="851cf-120">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="851cf-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="851cf-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="851cf-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="851cf-122">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="851cf-122">The call timed out.</span></span>|  
|<span data-ttu-id="851cf-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="851cf-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="851cf-124">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="851cf-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="851cf-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="851cf-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="851cf-126">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="851cf-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="851cf-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="851cf-127">E_FAIL</span></span>|<span data-ttu-id="851cf-128">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="851cf-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="851cf-129">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="851cf-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="851cf-130">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="851cf-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="851cf-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="851cf-131">E_INVALIDARG</span></span>|<span data-ttu-id="851cf-132">Pro zadanou hodnotu nelze nastavit časový limit `operation` nebo byla zadána neplatná hodnota pro `operation` .</span><span class="sxs-lookup"><span data-stu-id="851cf-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="851cf-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="851cf-133">Requirements</span></span>  
 <span data-ttu-id="851cf-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="851cf-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="851cf-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="851cf-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="851cf-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="851cf-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="851cf-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="851cf-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="851cf-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="851cf-138">See also</span></span>

- [<span data-ttu-id="851cf-139">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="851cf-139">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="851cf-140">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851cf-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="851cf-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851cf-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
