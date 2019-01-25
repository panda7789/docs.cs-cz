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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1497f1e08ab514c20fa82602f523aadb425303d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556467"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="55527-102">IHostPolicyManager::OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="55527-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="55527-103">Upozorňuje hostitele, který modul CLR (CLR) má provést výchozí akci, která byla nastavena voláním [iclrpolicymanager::setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metody v reakci na přerušení vlákna nebo <xref:System.AppDomain> uvolnit.</span><span class="sxs-lookup"><span data-stu-id="55527-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55527-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55527-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55527-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55527-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="55527-106">[in] Jeden z [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty určující druh událostí, ke kterému je CLR reagovat.</span><span class="sxs-lookup"><span data-stu-id="55527-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="55527-107">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty indikující akce, která trvá CLR v reakci na události.</span><span class="sxs-lookup"><span data-stu-id="55527-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55527-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="55527-108">Return Value</span></span>  
  
|<span data-ttu-id="55527-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55527-109">HRESULT</span></span>|<span data-ttu-id="55527-110">Popis</span><span class="sxs-lookup"><span data-stu-id="55527-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55527-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="55527-111">S_OK</span></span>|<span data-ttu-id="55527-112">`OnDefaultAction` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="55527-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="55527-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55527-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55527-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nemůže spouštět spravovaný kód a zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="55527-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="55527-115">úspěšně</span><span class="sxs-lookup"><span data-stu-id="55527-115">successfully</span></span>|  
|<span data-ttu-id="55527-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55527-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55527-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="55527-117">The call timed out.</span></span>|  
|<span data-ttu-id="55527-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55527-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55527-119">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="55527-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55527-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55527-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55527-121">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="55527-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55527-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55527-122">E_FAIL</span></span>|<span data-ttu-id="55527-123">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="55527-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55527-124">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="55527-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55527-125">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="55527-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55527-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55527-126">Requirements</span></span>  
 <span data-ttu-id="55527-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55527-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55527-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="55527-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55527-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55527-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55527-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55527-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55527-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55527-131">See also</span></span>
- [<span data-ttu-id="55527-132">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="55527-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="55527-133">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="55527-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="55527-134">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55527-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="55527-135">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55527-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
