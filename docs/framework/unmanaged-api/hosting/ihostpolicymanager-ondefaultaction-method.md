---
title: IHostPolicyManager::OnDefaultAction – metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: cdf0a720ac440d156b5b8bdc8dc2c78d3bb5ba86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128559"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="ff6a8-102">IHostPolicyManager::OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="ff6a8-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="ff6a8-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) se chystá převzít výchozí akci, která byla nastavena voláním metody [ICLRPolicyManager:: setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení vlákna nebo <xref:System.AppDomain> uvolnění.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff6a8-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff6a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff6a8-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="ff6a8-106">pro Jedna z hodnot [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , která označuje druh události, na kterou CLR reaguje.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="ff6a8-107">pro Jedna z hodnot [EPolicyAction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , která označuje akci, kterou modul CLR vezme v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff6a8-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff6a8-108">Return Value</span></span>  
  
|<span data-ttu-id="ff6a8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff6a8-109">HRESULT</span></span>|<span data-ttu-id="ff6a8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ff6a8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff6a8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff6a8-111">S_OK</span></span>|<span data-ttu-id="ff6a8-112">`OnDefaultAction` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="ff6a8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff6a8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff6a8-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="ff6a8-115">Nepodařilo</span><span class="sxs-lookup"><span data-stu-id="ff6a8-115">successfully</span></span>|  
|<span data-ttu-id="ff6a8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff6a8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff6a8-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-117">The call timed out.</span></span>|  
|<span data-ttu-id="ff6a8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff6a8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff6a8-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff6a8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff6a8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff6a8-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff6a8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff6a8-122">E_FAIL</span></span>|<span data-ttu-id="ff6a8-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff6a8-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff6a8-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff6a8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff6a8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff6a8-126">Requirements</span></span>  
 <span data-ttu-id="ff6a8-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff6a8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff6a8-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff6a8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff6a8-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ff6a8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff6a8-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff6a8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6a8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff6a8-131">See also</span></span>

- [<span data-ttu-id="ff6a8-132">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="ff6a8-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="ff6a8-133">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="ff6a8-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="ff6a8-134">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff6a8-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="ff6a8-135">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff6a8-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
