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
ms.openlocfilehash: c23773dce448c8c98d4926dff3fa51100e683fd0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192040"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="417a7-102">IHostControl::GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="417a7-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="417a7-103">Získá ukazatel rozhraní na implementaci rozhraní se zadaným `IID`.</span><span class="sxs-lookup"><span data-stu-id="417a7-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="417a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="417a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="417a7-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="417a7-106">pro `IID` rozhraní, pro které se modul CLR (Common Language Runtime) dotazuje na.</span><span class="sxs-lookup"><span data-stu-id="417a7-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="417a7-107">mimo Ukazatel na rozhraní implementovaného hostitelem nebo hodnotu null, pokud hostitel toto rozhraní nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="417a7-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="417a7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="417a7-108">Return Value</span></span>  
  
|<span data-ttu-id="417a7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="417a7-109">HRESULT</span></span>|<span data-ttu-id="417a7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="417a7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="417a7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="417a7-111">S_OK</span></span>|<span data-ttu-id="417a7-112">`GetHostManager` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="417a7-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="417a7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="417a7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="417a7-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="417a7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="417a7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="417a7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="417a7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="417a7-116">The call timed out.</span></span>|  
|<span data-ttu-id="417a7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="417a7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="417a7-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="417a7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="417a7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="417a7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="417a7-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="417a7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="417a7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="417a7-121">E_FAIL</span></span>|<span data-ttu-id="417a7-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="417a7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="417a7-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="417a7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="417a7-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="417a7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="417a7-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="417a7-125">E_INVALIDARG</span></span>|<span data-ttu-id="417a7-126">Požadovaná `IID` není platná.</span><span class="sxs-lookup"><span data-stu-id="417a7-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="417a7-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="417a7-127">E_NOINTERFACE</span></span>|<span data-ttu-id="417a7-128">Požadované rozhraní není podporováno.</span><span class="sxs-lookup"><span data-stu-id="417a7-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="417a7-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="417a7-129">Remarks</span></span>  
 <span data-ttu-id="417a7-130">CLR dotazuje hostitele, aby zjistil, zda podporuje jedno nebo více následujících rozhraní:</span><span class="sxs-lookup"><span data-stu-id="417a7-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="417a7-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="417a7-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="417a7-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="417a7-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="417a7-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="417a7-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="417a7-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="417a7-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="417a7-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="417a7-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="417a7-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="417a7-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="417a7-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="417a7-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="417a7-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="417a7-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="417a7-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="417a7-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="417a7-140">Pokud hostitel podporuje zadané rozhraní, nastaví `ppObject` ke své implementaci tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="417a7-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="417a7-141">V opačném případě nastaví `ppObject` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="417a7-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="417a7-142">CLR nevolá `Release` pro správce hostitele, ani když ho vypnete.</span><span class="sxs-lookup"><span data-stu-id="417a7-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="417a7-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="417a7-143">Requirements</span></span>  
 <span data-ttu-id="417a7-144">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="417a7-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="417a7-145">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="417a7-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="417a7-146">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="417a7-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="417a7-147">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="417a7-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417a7-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="417a7-148">See also</span></span>

- [<span data-ttu-id="417a7-149">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="417a7-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
