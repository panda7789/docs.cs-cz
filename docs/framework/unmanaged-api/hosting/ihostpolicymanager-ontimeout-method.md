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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88984da3e0456212c73280020da7235d136bf48b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482402"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="a63ba-102">IHostPolicyManager::OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="a63ba-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="a63ba-103">Upozorňuje hostitele, který modul CLR (CLR) má provést akce určená ve volání [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody v reakci na vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="a63ba-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63ba-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a63ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a63ba-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a63ba-106">[in] Jeden z [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty určující druh operace, která vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="a63ba-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="a63ba-107">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, udává akci CLR trvá v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="a63ba-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a63ba-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a63ba-108">Return Value</span></span>  
  
|<span data-ttu-id="a63ba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a63ba-109">HRESULT</span></span>|<span data-ttu-id="a63ba-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a63ba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a63ba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a63ba-111">S_OK</span></span>|<span data-ttu-id="a63ba-112">`OnTimeout` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a63ba-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a63ba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a63ba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a63ba-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a63ba-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a63ba-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a63ba-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a63ba-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a63ba-116">The call timed out.</span></span>|  
|<span data-ttu-id="a63ba-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a63ba-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a63ba-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a63ba-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a63ba-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a63ba-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a63ba-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a63ba-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a63ba-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a63ba-121">E_FAIL</span></span>|<span data-ttu-id="a63ba-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a63ba-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a63ba-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a63ba-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a63ba-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a63ba-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a63ba-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a63ba-125">Requirements</span></span>  
 <span data-ttu-id="a63ba-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63ba-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63ba-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a63ba-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a63ba-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a63ba-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a63ba-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63ba-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63ba-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a63ba-130">See also</span></span>
- [<span data-ttu-id="a63ba-131">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="a63ba-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a63ba-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="a63ba-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="a63ba-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63ba-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="a63ba-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a63ba-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
