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
ms.openlocfilehash: b6187da564a62b8c30abdc6a150f0df45d565615
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763868"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="00d67-102">IHostControl::GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="00d67-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="00d67-103">Získá ukazatel rozhraní k implementaci rozhraní hostitele se zadanou `IID`.</span><span class="sxs-lookup"><span data-stu-id="00d67-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d67-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="00d67-106">[in] `IID` Rozhraní, které modul CLR (CLR) je pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="00d67-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="00d67-107">[out] Ukazatel na rozhraní implementované hostitele, nebo hodnota null, pokud hostitel nepodporuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00d67-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00d67-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="00d67-108">Return Value</span></span>  
  
|<span data-ttu-id="00d67-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="00d67-109">HRESULT</span></span>|<span data-ttu-id="00d67-110">Popis</span><span class="sxs-lookup"><span data-stu-id="00d67-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00d67-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="00d67-111">S_OK</span></span>|<span data-ttu-id="00d67-112">`GetHostManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="00d67-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="00d67-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="00d67-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="00d67-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="00d67-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="00d67-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="00d67-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="00d67-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="00d67-116">The call timed out.</span></span>|  
|<span data-ttu-id="00d67-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="00d67-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="00d67-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="00d67-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="00d67-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="00d67-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="00d67-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="00d67-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="00d67-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="00d67-121">E_FAIL</span></span>|<span data-ttu-id="00d67-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="00d67-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="00d67-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="00d67-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="00d67-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="00d67-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="00d67-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="00d67-125">E_INVALIDARG</span></span>|<span data-ttu-id="00d67-126">Požadovaná `IID` není platný.</span><span class="sxs-lookup"><span data-stu-id="00d67-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="00d67-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="00d67-127">E_NOINTERFACE</span></span>|<span data-ttu-id="00d67-128">Požadované rozhraní není podporováno.</span><span class="sxs-lookup"><span data-stu-id="00d67-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00d67-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00d67-129">Remarks</span></span>  
 <span data-ttu-id="00d67-130">Modul CLR provádí dotazování hostitele k určení, jestli podporuje jednu nebo více z následujících rozhraní:</span><span class="sxs-lookup"><span data-stu-id="00d67-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="00d67-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="00d67-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="00d67-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="00d67-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="00d67-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="00d67-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="00d67-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="00d67-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="00d67-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="00d67-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="00d67-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="00d67-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="00d67-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="00d67-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="00d67-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="00d67-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="00d67-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="00d67-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="00d67-140">Pokud hostitel podporuje rozhraní zadané, nastaví `ppObject` k její implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00d67-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="00d67-141">Jinak, nastaví `ppObject` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="00d67-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="00d67-142">Modul CLR nevolá `Release` na správci hostitele, i v případě, že ji vypnout.</span><span class="sxs-lookup"><span data-stu-id="00d67-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d67-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00d67-143">Requirements</span></span>  
 <span data-ttu-id="00d67-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d67-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d67-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="00d67-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="00d67-146">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00d67-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00d67-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d67-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d67-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00d67-148">See also</span></span>

- [<span data-ttu-id="00d67-149">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00d67-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
