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
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178025"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="603b5-102">IHostPolicyManager::OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="603b5-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="603b5-103">Upozorní hostitele, že za běhu clr (common language) se chystá provést výchozí akci, která byla nastavena voláním metody [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení nebo <xref:System.AppDomain> uvolnění vlákna.</span><span class="sxs-lookup"><span data-stu-id="603b5-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="603b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="603b5-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="603b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="603b5-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="603b5-106">[v] Jedna z hodnot [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) označující druh události, na kterou odpovídá CLR.</span><span class="sxs-lookup"><span data-stu-id="603b5-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="603b5-107">[v] Jedna z hodnot [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) označující akci, kterou CLR provádí v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="603b5-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="603b5-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="603b5-108">Return Value</span></span>  
  
|<span data-ttu-id="603b5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="603b5-109">HRESULT</span></span>|<span data-ttu-id="603b5-110">Popis</span><span class="sxs-lookup"><span data-stu-id="603b5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="603b5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="603b5-111">S_OK</span></span>|<span data-ttu-id="603b5-112">`OnDefaultAction`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="603b5-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="603b5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="603b5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="603b5-114">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="603b5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="603b5-115">Úspěšně</span><span class="sxs-lookup"><span data-stu-id="603b5-115">successfully</span></span>|  
|<span data-ttu-id="603b5-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="603b5-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="603b5-117">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="603b5-117">The call timed out.</span></span>|  
|<span data-ttu-id="603b5-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="603b5-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="603b5-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="603b5-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="603b5-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="603b5-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="603b5-121">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="603b5-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="603b5-122">E_fail</span><span class="sxs-lookup"><span data-stu-id="603b5-122">E_FAIL</span></span>|<span data-ttu-id="603b5-123">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="603b5-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="603b5-124">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="603b5-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="603b5-125">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="603b5-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="603b5-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="603b5-126">Requirements</span></span>  
 <span data-ttu-id="603b5-127">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="603b5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="603b5-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="603b5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="603b5-129">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="603b5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="603b5-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="603b5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="603b5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="603b5-131">See also</span></span>

- [<span data-ttu-id="603b5-132">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="603b5-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="603b5-133">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="603b5-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="603b5-134">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="603b5-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="603b5-135">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="603b5-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
