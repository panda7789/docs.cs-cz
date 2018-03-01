---
title: "ICLRControl::SetAppDomainManagerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbddefa4211d63f012bce3532d7133b59c4ee1b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="0518e-102">ICLRControl::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="0518e-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="0518e-103">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="0518e-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0518e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0518e-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0518e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0518e-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="0518e-106">[v] Název sestavení, ve kterém na požadovaný typ odvozený z <xref:System.AppDomainManager> je implementována.</span><span class="sxs-lookup"><span data-stu-id="0518e-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="0518e-107">[v] Název typu implementované v `pwzAppDomainManagerAssembly` parametr, který implementuje možnosti <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="0518e-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0518e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0518e-108">Return Value</span></span>  
  
|<span data-ttu-id="0518e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0518e-109">HRESULT</span></span>|<span data-ttu-id="0518e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0518e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0518e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0518e-111">S_OK</span></span>|<span data-ttu-id="0518e-112">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0518e-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="0518e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0518e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0518e-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0518e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0518e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0518e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0518e-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0518e-116">The call timed out.</span></span>|  
|<span data-ttu-id="0518e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0518e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0518e-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0518e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0518e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0518e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0518e-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0518e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0518e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0518e-121">E_FAIL</span></span>|<span data-ttu-id="0518e-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0518e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0518e-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0518e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0518e-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0518e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0518e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0518e-125">Requirements</span></span>  
 <span data-ttu-id="0518e-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0518e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0518e-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0518e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0518e-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0518e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0518e-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0518e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0518e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0518e-130">See Also</span></span>  
 [<span data-ttu-id="0518e-131">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0518e-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="0518e-132">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0518e-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
