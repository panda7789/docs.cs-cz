---
title: IHostPolicyManager::OnTimeout – metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178008"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="54035-102">IHostPolicyManager::OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="54035-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="54035-103">Upozorní hostitele, že clr (CLR) společného jazyka se chystá provést akci určenou voláním metody [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na časový rozsah.</span><span class="sxs-lookup"><span data-stu-id="54035-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54035-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54035-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54035-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54035-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="54035-106">[v] Jedna z hodnot [EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) označující druh operace, která časový rozsah.</span><span class="sxs-lookup"><span data-stu-id="54035-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="54035-107">[v] Jedna z hodnot [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) označující akci, kterou CLR provádí v reakci na časový plán.</span><span class="sxs-lookup"><span data-stu-id="54035-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54035-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="54035-108">Return Value</span></span>  
  
|<span data-ttu-id="54035-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54035-109">HRESULT</span></span>|<span data-ttu-id="54035-110">Popis</span><span class="sxs-lookup"><span data-stu-id="54035-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54035-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="54035-111">S_OK</span></span>|<span data-ttu-id="54035-112">`OnTimeout`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="54035-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="54035-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54035-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54035-114">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="54035-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54035-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54035-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54035-116">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="54035-116">The call timed out.</span></span>|  
|<span data-ttu-id="54035-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54035-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54035-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="54035-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54035-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54035-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54035-120">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="54035-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54035-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="54035-121">E_FAIL</span></span>|<span data-ttu-id="54035-122">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="54035-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54035-123">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="54035-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54035-124">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="54035-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54035-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54035-125">Requirements</span></span>  
 <span data-ttu-id="54035-126">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54035-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54035-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54035-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54035-128">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54035-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54035-129">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54035-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54035-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="54035-130">See also</span></span>

- [<span data-ttu-id="54035-131">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="54035-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="54035-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="54035-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="54035-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54035-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="54035-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54035-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
