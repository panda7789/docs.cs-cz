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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87b4d4a9606723e5cf55fac19469809e1014b7c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439684"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="2c850-102">IHostPolicyManager::OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="2c850-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="2c850-103">Upozorní na hostitele, modul CLR (CLR) se chystá provést akci určenou volání [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda v reakci na selhání přidělení nebo recyklaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="2c850-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c850-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c850-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c850-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="2c850-106">[v] Jeden z [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty, která určuje typ selhání, ke kterému modulu CLR odpovídá.</span><span class="sxs-lookup"><span data-stu-id="2c850-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="2c850-107">[v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci modulu CLR trvá v reakci na `failure`.</span><span class="sxs-lookup"><span data-stu-id="2c850-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c850-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c850-108">Return Value</span></span>  
  
|<span data-ttu-id="2c850-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c850-109">HRESULT</span></span>|<span data-ttu-id="2c850-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2c850-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c850-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c850-111">S_OK</span></span>|<span data-ttu-id="2c850-112">`OnFailure` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2c850-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="2c850-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c850-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c850-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2c850-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c850-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c850-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c850-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2c850-116">The call timed out.</span></span>|  
|<span data-ttu-id="2c850-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c850-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c850-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2c850-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c850-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c850-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c850-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2c850-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c850-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c850-121">E_FAIL</span></span>|<span data-ttu-id="2c850-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2c850-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c850-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2c850-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c850-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c850-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c850-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c850-125">Requirements</span></span>  
 <span data-ttu-id="2c850-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c850-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c850-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c850-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c850-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c850-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c850-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c850-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c850-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c850-130">See Also</span></span>  
 [<span data-ttu-id="2c850-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="2c850-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="2c850-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="2c850-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="2c850-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c850-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="2c850-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c850-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
