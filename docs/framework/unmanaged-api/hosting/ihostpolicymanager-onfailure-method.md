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
ms.openlocfilehash: 78d2b84598a034bf6c534745bcb99a080d039617
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100324"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="8b0ef-102">IHostPolicyManager::OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="8b0ef-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="8b0ef-103">Upozorňuje hostitele, který modul CLR (CLR) má provést akce určená ve volání [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody v reakci na selhání přidělení nebo recyklaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b0ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b0ef-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b0ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b0ef-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="8b0ef-106">[in] Jeden z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty určující druh selhání, ke kterému je CLR reagovat.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="8b0ef-107">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, udává akci CLR trvá v reakci na `failure`.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b0ef-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8b0ef-108">Return Value</span></span>  
  
|<span data-ttu-id="8b0ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b0ef-109">HRESULT</span></span>|<span data-ttu-id="8b0ef-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8b0ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b0ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b0ef-111">S_OK</span></span>|<span data-ttu-id="8b0ef-112">`OnFailure` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="8b0ef-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b0ef-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b0ef-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b0ef-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b0ef-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b0ef-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-116">The call timed out.</span></span>|  
|<span data-ttu-id="8b0ef-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b0ef-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b0ef-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b0ef-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b0ef-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b0ef-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b0ef-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b0ef-121">E_FAIL</span></span>|<span data-ttu-id="8b0ef-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b0ef-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b0ef-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8b0ef-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b0ef-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b0ef-125">Requirements</span></span>  
 <span data-ttu-id="8b0ef-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b0ef-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b0ef-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b0ef-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b0ef-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b0ef-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b0ef-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b0ef-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0ef-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b0ef-130">See also</span></span>

- [<span data-ttu-id="8b0ef-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="8b0ef-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="8b0ef-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="8b0ef-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="8b0ef-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b0ef-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8b0ef-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b0ef-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
