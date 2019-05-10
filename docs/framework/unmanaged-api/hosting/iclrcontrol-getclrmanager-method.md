---
title: ICLRControl::GetCLRManager – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97d75eb5fab396530a6f48314e96c8d47d06439
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656485"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="c2549-102">ICLRControl::GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="c2549-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="c2549-103">Získá ukazatel rozhraní k instanci správce typy, které hostitele můžete použít ke konfiguraci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c2549-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2549-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2549-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2549-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="c2549-106">[in] `IID` Typu správce, který vrátí.</span><span class="sxs-lookup"><span data-stu-id="c2549-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="c2549-107">Následující `IID` hodnoty jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c2549-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="c2549-108">IID_ICLRDebugManager: Určuje, že `ppObject` typu [iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-109">IID_ICLRErrorReportingManager: Určuje, že `ppObject` typu [iclrerrorreportingmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-110">IID_ICLRGCManager: Určuje, že `ppObject` typu [iclrgcmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-111">IID_ICLRHostProtectionManager: Určuje, že `ppObject` typu [iclrhostprotectionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-112">IID_ICLROnEventManager: Určuje, že `ppObject` typu [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-113">IID_ICLRPolicyManager: Určuje, že `ppObject` typu [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="c2549-114">IID_ICLRTaskManager: Určuje, že `ppObject` typu [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c2549-115">[out] Ukazatel rozhraní na požadovaný správce nebo hodnota null, pokud byl požadován typ neplatného správce.</span><span class="sxs-lookup"><span data-stu-id="c2549-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2549-116">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2549-116">Return Value</span></span>  
  
|<span data-ttu-id="c2549-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2549-117">HRESULT</span></span>|<span data-ttu-id="c2549-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c2549-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2549-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2549-119">S_OK</span></span>|<span data-ttu-id="c2549-120">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c2549-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="c2549-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c2549-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c2549-122">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c2549-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c2549-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c2549-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c2549-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c2549-124">The call timed out.</span></span>|  
|<span data-ttu-id="c2549-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c2549-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c2549-126">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c2549-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c2549-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c2549-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c2549-128">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c2549-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c2549-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c2549-129">E_FAIL</span></span>|<span data-ttu-id="c2549-130">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c2549-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c2549-131">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c2549-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c2549-132">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2549-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c2549-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="c2549-133">E_NOINTERFACE</span></span>|<span data-ttu-id="c2549-134">Typ rozhraní není podporován.</span><span class="sxs-lookup"><span data-stu-id="c2549-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2549-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2549-135">Requirements</span></span>  
 <span data-ttu-id="c2549-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2549-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2549-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2549-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2549-138">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2549-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2549-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2549-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2549-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2549-140">See also</span></span>

- [<span data-ttu-id="c2549-141">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2549-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c2549-142">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2549-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
