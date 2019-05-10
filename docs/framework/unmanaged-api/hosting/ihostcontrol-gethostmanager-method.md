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
ms.openlocfilehash: e51ff24698a2839972f9a36eac6c18d4f6709ebd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600154"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="ee536-102">IHostControl::GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="ee536-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="ee536-103">Získá ukazatel rozhraní k implementaci rozhraní hostitele se zadanou `IID`.</span><span class="sxs-lookup"><span data-stu-id="ee536-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee536-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee536-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee536-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="ee536-106">[in] `IID` Rozhraní, které modul CLR (CLR) je pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="ee536-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="ee536-107">[out] Ukazatel na rozhraní implementované hostitele, nebo hodnota null, pokud hostitel nepodporuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee536-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee536-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee536-108">Return Value</span></span>  
  
|<span data-ttu-id="ee536-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee536-109">HRESULT</span></span>|<span data-ttu-id="ee536-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ee536-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee536-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee536-111">S_OK</span></span>|<span data-ttu-id="ee536-112">`GetHostManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ee536-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="ee536-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ee536-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ee536-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ee536-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ee536-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee536-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ee536-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ee536-116">The call timed out.</span></span>|  
|<span data-ttu-id="ee536-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ee536-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ee536-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="ee536-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ee536-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ee536-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ee536-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="ee536-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ee536-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ee536-121">E_FAIL</span></span>|<span data-ttu-id="ee536-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="ee536-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ee536-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ee536-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ee536-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ee536-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ee536-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ee536-125">E_INVALIDARG</span></span>|<span data-ttu-id="ee536-126">Požadovaná `IID` není platný.</span><span class="sxs-lookup"><span data-stu-id="ee536-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="ee536-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="ee536-127">E_NOINTERFACE</span></span>|<span data-ttu-id="ee536-128">Požadované rozhraní není podporováno.</span><span class="sxs-lookup"><span data-stu-id="ee536-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee536-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee536-129">Remarks</span></span>  
 <span data-ttu-id="ee536-130">Modul CLR provádí dotazování hostitele k určení, jestli podporuje jednu nebo více z následujících rozhraní:</span><span class="sxs-lookup"><span data-stu-id="ee536-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="ee536-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="ee536-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="ee536-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="ee536-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="ee536-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="ee536-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="ee536-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="ee536-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="ee536-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="ee536-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="ee536-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="ee536-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="ee536-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="ee536-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="ee536-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ee536-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="ee536-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="ee536-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="ee536-140">Pokud hostitel podporuje rozhraní zadané, nastaví `ppObject` k její implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee536-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="ee536-141">Jinak, nastaví `ppObject` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ee536-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="ee536-142">Modul CLR nevolá `Release` na správci hostitele, i v případě, že ji vypnout.</span><span class="sxs-lookup"><span data-stu-id="ee536-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee536-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee536-143">Requirements</span></span>  
 <span data-ttu-id="ee536-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee536-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee536-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee536-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee536-146">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee536-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee536-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee536-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee536-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee536-148">See also</span></span>

- [<span data-ttu-id="ee536-149">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee536-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
