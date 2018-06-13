---
title: IHostControl::GetHostManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 355d2e259adb13da44b09e19872337c17ac20ade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439319"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="03e98-102">IHostControl::GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="03e98-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="03e98-103">Získá ukazatele rozhraní hostitele implementaci rozhraní se zadaným `IID`.</span><span class="sxs-lookup"><span data-stu-id="03e98-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03e98-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03e98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03e98-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="03e98-106">[v] `IID` Rozhraní, které je dotazování common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="03e98-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="03e98-107">[out] Ukazatel rozhraní implementované hostitele nebo hodnota null, pokud hostitel nepodporuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03e98-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03e98-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03e98-108">Return Value</span></span>  
  
|<span data-ttu-id="03e98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03e98-109">HRESULT</span></span>|<span data-ttu-id="03e98-110">Popis</span><span class="sxs-lookup"><span data-stu-id="03e98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03e98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="03e98-111">S_OK</span></span>|<span data-ttu-id="03e98-112">`GetHostManager` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="03e98-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="03e98-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03e98-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03e98-114">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="03e98-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="03e98-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="03e98-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="03e98-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="03e98-116">The call timed out.</span></span>|  
|<span data-ttu-id="03e98-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="03e98-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="03e98-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="03e98-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="03e98-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="03e98-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="03e98-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="03e98-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="03e98-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03e98-121">E_FAIL</span></span>|<span data-ttu-id="03e98-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="03e98-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="03e98-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="03e98-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="03e98-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="03e98-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03e98-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="03e98-125">E_INVALIDARG</span></span>|<span data-ttu-id="03e98-126">Požadovanou `IID` není platný.</span><span class="sxs-lookup"><span data-stu-id="03e98-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="03e98-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="03e98-127">E_NOINTERFACE</span></span>|<span data-ttu-id="03e98-128">Nepodporuje požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03e98-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03e98-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03e98-129">Remarks</span></span>  
 <span data-ttu-id="03e98-130">Modul CLR dotazuje na hostiteli a zjistit, jestli podporuje jeden nebo více z následujících rozhraní:</span><span class="sxs-lookup"><span data-stu-id="03e98-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="03e98-131">Ihostmemorymanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="03e98-132">Ihosttaskmanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="03e98-133">Ihostthreadpoolmanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="03e98-134">Ihostiocompletionmanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="03e98-135">Ihostsyncmanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="03e98-136">Ihostassemblymanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="03e98-137">Ihostgcmanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="03e98-138">Ihostpolicymanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="03e98-139">Ihostsecuritymanager –</span><span class="sxs-lookup"><span data-stu-id="03e98-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="03e98-140">Pokud hostitel podporuje rozhraní zadané, nastaví `ppObject` její implementace tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03e98-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="03e98-141">Jinak, nastaví `ppObject` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="03e98-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="03e98-142">Modul CLR nevyvolá `Release` hostitele manažerů, i když ho vypnout.</span><span class="sxs-lookup"><span data-stu-id="03e98-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e98-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03e98-143">Requirements</span></span>  
 <span data-ttu-id="03e98-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e98-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e98-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03e98-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03e98-146">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03e98-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03e98-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e98-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e98-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="03e98-148">See Also</span></span>  
 [<span data-ttu-id="03e98-149">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03e98-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
