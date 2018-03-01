---
title: "ICLRControl::GetCLRManager – metoda"
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
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 197a3818de8d0b17331a9f9ac422ecaabb230a50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="95e24-102">ICLRControl::GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="95e24-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="95e24-103">Získá ukazatele rozhraní k instanci jakýkoli z typů správce, které hostitele můžete použít ke konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="95e24-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95e24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95e24-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95e24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95e24-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="95e24-106">[v] `IID` Typu manager vrátit.</span><span class="sxs-lookup"><span data-stu-id="95e24-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="95e24-107">Následující `IID` hodnoty jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="95e24-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="95e24-108">IID_ICLRDebugManager: Určuje, že `ppObject` bude typu [iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-109">IID_ICLRErrorReportingManager: Určuje, že `ppObject` bude typu [iclrerrorreportingmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-110">IID_ICLRGCManager: Určuje, že `ppObject` bude typu [iclrgcmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-111">IID_ICLRHostProtectionManager: Určuje, že `ppObject` bude typu [iclrhostprotectionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-112">IID_ICLROnEventManager: Určuje, že `ppObject` bude typu [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-113">IID_ICLRPolicyManager: Určuje, že `ppObject` bude typu [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="95e24-114">IID_ICLRTaskManager: speciries, `ppObject` bude typu [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="95e24-115">[out] Ukazatel rozhraní požadovaný manager, nebo hodnotu null, pokud byl požadován typ neplatného správce.</span><span class="sxs-lookup"><span data-stu-id="95e24-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95e24-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95e24-116">Return Value</span></span>  
  
|<span data-ttu-id="95e24-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95e24-117">HRESULT</span></span>|<span data-ttu-id="95e24-118">Popis</span><span class="sxs-lookup"><span data-stu-id="95e24-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95e24-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="95e24-119">S_OK</span></span>|<span data-ttu-id="95e24-120">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="95e24-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="95e24-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95e24-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95e24-122">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="95e24-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95e24-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95e24-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95e24-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="95e24-124">The call timed out.</span></span>|  
|<span data-ttu-id="95e24-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95e24-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95e24-126">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="95e24-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95e24-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95e24-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95e24-128">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="95e24-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95e24-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95e24-129">E_FAIL</span></span>|<span data-ttu-id="95e24-130">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="95e24-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95e24-131">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="95e24-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95e24-132">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="95e24-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95e24-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="95e24-133">E_NOINTERFACE</span></span>|<span data-ttu-id="95e24-134">Typ rozhraní není podporován.</span><span class="sxs-lookup"><span data-stu-id="95e24-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95e24-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95e24-135">Requirements</span></span>  
 <span data-ttu-id="95e24-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95e24-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95e24-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95e24-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95e24-138">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95e24-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95e24-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95e24-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e24-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="95e24-140">See Also</span></span>  
 [<span data-ttu-id="95e24-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e24-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="95e24-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95e24-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
