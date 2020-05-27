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
ms.openlocfilehash: fb0f943d710322257d052edc5c16108671622790
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804217"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="b9334-102">IHostPolicyManager::OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="b9334-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="b9334-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) se chystá provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="b9334-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9334-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9334-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9334-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9334-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b9334-106">pro Jedna z hodnot [EClrOperation –](eclroperation-enumeration.md) , která indikuje druh operace, která vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="b9334-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="b9334-107">pro Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) , která označuje akci, kterou modul CLR vezme v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="b9334-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9334-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9334-108">Return Value</span></span>  
  
|<span data-ttu-id="b9334-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9334-109">HRESULT</span></span>|<span data-ttu-id="b9334-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b9334-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9334-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9334-111">S_OK</span></span>|<span data-ttu-id="b9334-112">`OnTimeout`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b9334-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="b9334-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b9334-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b9334-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b9334-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b9334-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b9334-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b9334-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b9334-116">The call timed out.</span></span>|  
|<span data-ttu-id="b9334-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b9334-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b9334-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b9334-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b9334-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b9334-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b9334-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b9334-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b9334-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9334-121">E_FAIL</span></span>|<span data-ttu-id="b9334-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b9334-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b9334-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b9334-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b9334-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b9334-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9334-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9334-125">Requirements</span></span>  
 <span data-ttu-id="b9334-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9334-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9334-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b9334-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9334-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9334-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9334-129">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9334-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9334-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9334-130">See also</span></span>

- [<span data-ttu-id="b9334-131">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="b9334-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="b9334-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="b9334-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="b9334-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9334-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="b9334-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9334-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
