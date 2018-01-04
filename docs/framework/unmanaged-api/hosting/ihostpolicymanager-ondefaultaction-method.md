---
title: "IHostPolicyManager::OnDefaultAction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1fded3d986e6505d0a321c47b03b5cdf9d881a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="46304-102">IHostPolicyManager::OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="46304-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="46304-103">Upozorní hostitele, který modul CLR (CLR) se chystáte udělat výchozí akci, která byla nastavena voláním [iclrpolicymanager::setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metoda v reakci na vlákno přerušení nebo <xref:System.AppDomain> uvolnit.</span><span class="sxs-lookup"><span data-stu-id="46304-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46304-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46304-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="46304-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="46304-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="46304-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje druh událostí, ke kterému modulu CLR odpovídá.</span><span class="sxs-lookup"><span data-stu-id="46304-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="46304-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci, která modulu CLR trvá v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="46304-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46304-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="46304-108">Return Value</span></span>  
  
|<span data-ttu-id="46304-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46304-109">HRESULT</span></span>|<span data-ttu-id="46304-110">Popis</span><span class="sxs-lookup"><span data-stu-id="46304-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46304-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="46304-111">S_OK</span></span>|<span data-ttu-id="46304-112">`OnDefaultAction`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="46304-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="46304-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46304-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46304-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže spustit spravovaného kódu nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="46304-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="46304-115">úspěšně</span><span class="sxs-lookup"><span data-stu-id="46304-115">successfully</span></span>|  
|<span data-ttu-id="46304-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46304-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46304-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="46304-117">The call timed out.</span></span>|  
|<span data-ttu-id="46304-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46304-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46304-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="46304-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46304-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46304-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46304-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="46304-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46304-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46304-122">E_FAIL</span></span>|<span data-ttu-id="46304-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="46304-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46304-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="46304-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46304-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="46304-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46304-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46304-126">Requirements</span></span>  
 <span data-ttu-id="46304-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46304-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46304-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="46304-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46304-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="46304-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46304-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46304-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46304-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="46304-131">See Also</span></span>  
 [<span data-ttu-id="46304-132">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="46304-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="46304-133">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="46304-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="46304-134">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46304-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="46304-135">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46304-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
