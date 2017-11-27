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
ms.openlocfilehash: ca5eb767c08733980c9156d04526594c62349624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="13586-102">IHostPolicyManager::OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="13586-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="13586-103">Upozorní hostitele, který modul CLR (CLR) se chystáte udělat výchozí akci, která byla nastavena voláním [iclrpolicymanager::setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) metoda v reakci na vlákno přerušení nebo <xref:System.AppDomain> uvolnit.</span><span class="sxs-lookup"><span data-stu-id="13586-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13586-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13586-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13586-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13586-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="13586-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje druh událostí, ke kterému modulu CLR odpovídá.</span><span class="sxs-lookup"><span data-stu-id="13586-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="13586-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci, která modulu CLR trvá v reakci na událost.</span><span class="sxs-lookup"><span data-stu-id="13586-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13586-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="13586-108">Return Value</span></span>  
  
|<span data-ttu-id="13586-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13586-109">HRESULT</span></span>|<span data-ttu-id="13586-110">Popis</span><span class="sxs-lookup"><span data-stu-id="13586-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13586-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="13586-111">S_OK</span></span>|<span data-ttu-id="13586-112">`OnDefaultAction`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="13586-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="13586-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13586-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13586-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže spustit spravovaného kódu nebo zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="13586-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="13586-115">úspěšně</span><span class="sxs-lookup"><span data-stu-id="13586-115">successfully</span></span>|  
|<span data-ttu-id="13586-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13586-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13586-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="13586-117">The call timed out.</span></span>|  
|<span data-ttu-id="13586-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13586-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13586-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="13586-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13586-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13586-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13586-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="13586-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13586-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13586-122">E_FAIL</span></span>|<span data-ttu-id="13586-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="13586-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13586-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="13586-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13586-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13586-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13586-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13586-126">Requirements</span></span>  
 <span data-ttu-id="13586-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13586-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13586-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13586-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13586-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="13586-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13586-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13586-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13586-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="13586-131">See Also</span></span>  
 [<span data-ttu-id="13586-132">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="13586-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="13586-133">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="13586-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="13586-134">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13586-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="13586-135">Ihostpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13586-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
