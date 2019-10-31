---
title: IHostPolicyManager::OnFailure – metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: 3bb65d747d7cdc81bd534108f6189eb1c94e3b15
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128547"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="e46a2-102">IHostPolicyManager::OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="e46a2-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="e46a2-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) se chystá provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnFailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.</span><span class="sxs-lookup"><span data-stu-id="e46a2-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e46a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e46a2-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e46a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e46a2-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="e46a2-106">pro Jedna z hodnot [EClrFailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) , která označuje druh selhání, na který CLR reaguje.</span><span class="sxs-lookup"><span data-stu-id="e46a2-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="e46a2-107">pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , která označuje akci, kterou modul CLR vezme v reakci na `failure`.</span><span class="sxs-lookup"><span data-stu-id="e46a2-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e46a2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e46a2-108">Return Value</span></span>  
  
|<span data-ttu-id="e46a2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e46a2-109">HRESULT</span></span>|<span data-ttu-id="e46a2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e46a2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e46a2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e46a2-111">S_OK</span></span>|<span data-ttu-id="e46a2-112">`OnFailure` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e46a2-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="e46a2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e46a2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e46a2-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e46a2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e46a2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e46a2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e46a2-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e46a2-116">The call timed out.</span></span>|  
|<span data-ttu-id="e46a2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e46a2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e46a2-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="e46a2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e46a2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e46a2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e46a2-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="e46a2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e46a2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e46a2-121">E_FAIL</span></span>|<span data-ttu-id="e46a2-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="e46a2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e46a2-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="e46a2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e46a2-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e46a2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e46a2-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e46a2-125">Requirements</span></span>  
 <span data-ttu-id="e46a2-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e46a2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e46a2-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e46a2-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e46a2-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e46a2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e46a2-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e46a2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e46a2-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e46a2-130">See also</span></span>

- [<span data-ttu-id="e46a2-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="e46a2-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="e46a2-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="e46a2-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="e46a2-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e46a2-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="e46a2-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e46a2-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
