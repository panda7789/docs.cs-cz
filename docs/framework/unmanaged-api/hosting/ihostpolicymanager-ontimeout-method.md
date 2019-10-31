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
ms.openlocfilehash: e8a14dd6a6d196cea9caa6be669b2b75a167eca8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141109"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="741a9-102">IHostPolicyManager::OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="741a9-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="741a9-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) se chystá provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="741a9-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="741a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="741a9-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="741a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="741a9-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="741a9-106">pro Jedna z hodnot [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , která indikuje druh operace, která vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="741a9-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="741a9-107">pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , která označuje akci, kterou modul CLR vezme v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="741a9-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="741a9-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="741a9-108">Return Value</span></span>  
  
|<span data-ttu-id="741a9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="741a9-109">HRESULT</span></span>|<span data-ttu-id="741a9-110">Popis</span><span class="sxs-lookup"><span data-stu-id="741a9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="741a9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="741a9-111">S_OK</span></span>|<span data-ttu-id="741a9-112">`OnTimeout` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="741a9-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="741a9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="741a9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="741a9-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="741a9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="741a9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="741a9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="741a9-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="741a9-116">The call timed out.</span></span>|  
|<span data-ttu-id="741a9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="741a9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="741a9-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="741a9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="741a9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="741a9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="741a9-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="741a9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="741a9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="741a9-121">E_FAIL</span></span>|<span data-ttu-id="741a9-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="741a9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="741a9-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="741a9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="741a9-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="741a9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="741a9-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="741a9-125">Requirements</span></span>  
 <span data-ttu-id="741a9-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="741a9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="741a9-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="741a9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="741a9-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="741a9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="741a9-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="741a9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741a9-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="741a9-130">See also</span></span>

- [<span data-ttu-id="741a9-131">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="741a9-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="741a9-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="741a9-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="741a9-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="741a9-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="741a9-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="741a9-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
