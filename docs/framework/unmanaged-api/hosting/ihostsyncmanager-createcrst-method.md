---
title: IHostSyncManager::CreateCrst – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 622b6c523adfb7bae2fc38826152ef69709568cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931079"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="d08b9-102">IHostSyncManager::CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="d08b9-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="d08b9-103">Vytvoří objekt kritického oddílu pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="d08b9-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d08b9-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d08b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d08b9-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="d08b9-106">mimo Ukazatel na adresu instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) implementované hostitelem nebo hodnotu null, pokud nelze vytvořit oddíl Critical.</span><span class="sxs-lookup"><span data-stu-id="d08b9-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d08b9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d08b9-107">Return Value</span></span>  
  
|<span data-ttu-id="d08b9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d08b9-108">HRESULT</span></span>|<span data-ttu-id="d08b9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d08b9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d08b9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d08b9-110">S_OK</span></span>|<span data-ttu-id="d08b9-111">`CreateCrst`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d08b9-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="d08b9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d08b9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d08b9-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d08b9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d08b9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d08b9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d08b9-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d08b9-115">The call timed out.</span></span>|  
|<span data-ttu-id="d08b9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d08b9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d08b9-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d08b9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d08b9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d08b9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d08b9-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d08b9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d08b9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d08b9-120">E_FAIL</span></span>|<span data-ttu-id="d08b9-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d08b9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d08b9-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d08b9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d08b9-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d08b9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d08b9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d08b9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d08b9-125">Pro vytvoření požadovaného kritického oddílu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="d08b9-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08b9-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d08b9-126">Remarks</span></span>  
 <span data-ttu-id="d08b9-127">Klíčové objekty oddílu poskytují synchronizaci podobnou té, kterou poskytuje objekt mutex, s tím rozdílem, že kritické oddíly mohou být použity pouze vlákny jednoho procesu.</span><span class="sxs-lookup"><span data-stu-id="d08b9-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="d08b9-128">`CreateCrst`zrcadlí funkci `InitializeCriticalSection` Win32.</span><span class="sxs-lookup"><span data-stu-id="d08b9-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08b9-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d08b9-129">Requirements</span></span>  
 <span data-ttu-id="d08b9-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d08b9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08b9-131">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d08b9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d08b9-132">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d08b9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d08b9-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08b9-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08b9-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d08b9-134">See also</span></span>

- [<span data-ttu-id="d08b9-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d08b9-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d08b9-136">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d08b9-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="d08b9-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d08b9-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="d08b9-138">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d08b9-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="d08b9-139">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="d08b9-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="d08b9-140">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="d08b9-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
