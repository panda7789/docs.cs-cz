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
ms.openlocfilehash: f3187a72d4b05be8d7b5b49df149366c4beb11d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779603"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="fd1ed-102">IHostPolicyManager::OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="fd1ed-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="fd1ed-103">Upozorňuje hostitele, který modul CLR (CLR) má provést akce určená ve volání [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody v reakci na selhání přidělení nebo recyklaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd1ed-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd1ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd1ed-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="fd1ed-106">[in] Jeden z [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) hodnoty určující druh selhání, ke kterému je CLR reagovat.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="fd1ed-107">[in] Jeden z [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, udává akci CLR trvá v reakci na `failure`.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd1ed-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fd1ed-108">Return Value</span></span>  
  
|<span data-ttu-id="fd1ed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd1ed-109">HRESULT</span></span>|<span data-ttu-id="fd1ed-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fd1ed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd1ed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd1ed-111">S_OK</span></span>|<span data-ttu-id="fd1ed-112">`OnFailure` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="fd1ed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd1ed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd1ed-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd1ed-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd1ed-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd1ed-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-116">The call timed out.</span></span>|  
|<span data-ttu-id="fd1ed-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd1ed-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd1ed-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd1ed-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd1ed-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd1ed-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd1ed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd1ed-121">E_FAIL</span></span>|<span data-ttu-id="fd1ed-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd1ed-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd1ed-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd1ed-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd1ed-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd1ed-125">Requirements</span></span>  
 <span data-ttu-id="fd1ed-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd1ed-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd1ed-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd1ed-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd1ed-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd1ed-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd1ed-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd1ed-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1ed-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd1ed-130">See also</span></span>

- [<span data-ttu-id="fd1ed-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="fd1ed-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="fd1ed-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="fd1ed-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="fd1ed-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd1ed-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="fd1ed-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd1ed-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
