---
title: "ICLRControl::SetAppDomainManagerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6632417cb0cfe17d7bde16ecf47ae1c001f43f2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="56718-102">ICLRControl::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="56718-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="56718-103">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="56718-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56718-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56718-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56718-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56718-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="56718-106">[v] Název sestavení, ve kterém na požadovaný typ odvozený z <xref:System.AppDomainManager> je implementována.</span><span class="sxs-lookup"><span data-stu-id="56718-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="56718-107">[v] Název typu implementované v `pwzAppDomainManagerAssembly` parametr, který implementuje možnosti <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="56718-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56718-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56718-108">Return Value</span></span>  
  
|<span data-ttu-id="56718-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56718-109">HRESULT</span></span>|<span data-ttu-id="56718-110">Popis</span><span class="sxs-lookup"><span data-stu-id="56718-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56718-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="56718-111">S_OK</span></span>|<span data-ttu-id="56718-112">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="56718-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="56718-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56718-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56718-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="56718-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56718-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56718-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56718-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="56718-116">The call timed out.</span></span>|  
|<span data-ttu-id="56718-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56718-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56718-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="56718-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56718-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56718-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56718-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="56718-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56718-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56718-121">E_FAIL</span></span>|<span data-ttu-id="56718-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="56718-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56718-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="56718-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56718-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="56718-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56718-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56718-125">Requirements</span></span>  
 <span data-ttu-id="56718-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56718-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56718-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56718-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56718-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56718-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56718-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56718-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56718-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="56718-130">See Also</span></span>  
 [<span data-ttu-id="56718-131">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56718-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="56718-132">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56718-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
