---
title: "IHostControl::SetAppDomainManager – metoda"
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
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d689a664f5bad19a70a8d635beb1f25f33da6ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="854cb-102">IHostControl::SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="854cb-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="854cb-103">Upozorní hostitele vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="854cb-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="854cb-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="854cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="854cb-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="854cb-106">[v] Číselný identifikátor vybrané <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="854cb-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="854cb-107">[v] Ukazatel <xref:System.AppDomainManager> objekt, který implementuje hostitele jako `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="854cb-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="854cb-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="854cb-108">Return Value</span></span>  
  
|<span data-ttu-id="854cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="854cb-109">HRESULT</span></span>|<span data-ttu-id="854cb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="854cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="854cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="854cb-111">S_OK</span></span>|<span data-ttu-id="854cb-112">`SetAppDomainManager`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="854cb-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="854cb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="854cb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="854cb-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="854cb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="854cb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="854cb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="854cb-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="854cb-116">The call timed out.</span></span>|  
|<span data-ttu-id="854cb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="854cb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="854cb-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="854cb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="854cb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="854cb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="854cb-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="854cb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="854cb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="854cb-121">E_FAIL</span></span>|<span data-ttu-id="854cb-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="854cb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="854cb-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="854cb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="854cb-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="854cb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="854cb-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="854cb-125">Remarks</span></span>  
 <span data-ttu-id="854cb-126"><xref:System.AppDomainManager> Hostitel poskytuje mechanismus k navázání připojení do spravovaného kódu a k řízení vytvoření a nastavení jednotlivých <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="854cb-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="854cb-127"><xref:System.AppDomainManager> Je načten do každé <xref:System.AppDomain> při který <xref:System.AppDomain> je vytvořena.</span><span class="sxs-lookup"><span data-stu-id="854cb-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="854cb-128">Pokud se rozhodne, modulu CLR upozorní hostitele domény aplikace vytvořila nastavením hodnoty `pUnkAppDomainManager` parametr.</span><span class="sxs-lookup"><span data-stu-id="854cb-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="854cb-129">Při implementaci `SetAppDomainManager` metody hostitele můžete nastavit název sestavení a typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="854cb-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854cb-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="854cb-130">Requirements</span></span>  
 <span data-ttu-id="854cb-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="854cb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="854cb-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="854cb-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="854cb-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="854cb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="854cb-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="854cb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854cb-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="854cb-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="854cb-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="854cb-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
