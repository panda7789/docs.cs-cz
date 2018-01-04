---
title: "IHostPolicyManager::OnTimeout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b8c29bc281b64368e8b310e2b13f3fcb1bdc6ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="83e9f-102">IHostPolicyManager::OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="83e9f-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="83e9f-103">Upozorní na hostitele, modul CLR (CLR) se chystá provést akci určenou volání [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metoda v reakci na vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="83e9f-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e9f-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83e9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83e9f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="83e9f-106">[v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, označující typ operace vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="83e9f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="83e9f-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci modulu CLR trvá v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="83e9f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83e9f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="83e9f-108">Return Value</span></span>  
  
|<span data-ttu-id="83e9f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83e9f-109">HRESULT</span></span>|<span data-ttu-id="83e9f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="83e9f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83e9f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="83e9f-111">S_OK</span></span>|<span data-ttu-id="83e9f-112">`OnTimeout`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="83e9f-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="83e9f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83e9f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83e9f-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="83e9f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83e9f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83e9f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83e9f-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="83e9f-116">The call timed out.</span></span>|  
|<span data-ttu-id="83e9f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83e9f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83e9f-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="83e9f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83e9f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83e9f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83e9f-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="83e9f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83e9f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83e9f-121">E_FAIL</span></span>|<span data-ttu-id="83e9f-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="83e9f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83e9f-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="83e9f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83e9f-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83e9f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83e9f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83e9f-125">Requirements</span></span>  
 <span data-ttu-id="83e9f-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e9f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e9f-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83e9f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83e9f-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83e9f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83e9f-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e9f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e9f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="83e9f-130">See Also</span></span>  
 [<span data-ttu-id="83e9f-131">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="83e9f-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="83e9f-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="83e9f-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="83e9f-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83e9f-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="83e9f-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="83e9f-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
