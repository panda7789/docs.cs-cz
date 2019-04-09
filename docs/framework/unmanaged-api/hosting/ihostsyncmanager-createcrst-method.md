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
ms.openlocfilehash: 8b63b283a28ed27a70698c45bdc87d63fef0daf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117938"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="784ab-102">IHostSyncManager::CreateCrst – metoda</span><span class="sxs-lookup"><span data-stu-id="784ab-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="784ab-103">Vytvoří objekt kritický oddíl pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="784ab-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="784ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="784ab-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="784ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="784ab-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="784ab-106">[out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci implementovaného tímto hostitelem, nebo hodnotu null, pokud nebylo možné vytvořit kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="784ab-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="784ab-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="784ab-107">Return Value</span></span>  
  
|<span data-ttu-id="784ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="784ab-108">HRESULT</span></span>|<span data-ttu-id="784ab-109">Popis</span><span class="sxs-lookup"><span data-stu-id="784ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="784ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="784ab-110">S_OK</span></span>|`CreateCrst` <span data-ttu-id="784ab-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="784ab-111">returned successfully.</span></span>|  
|<span data-ttu-id="784ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="784ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="784ab-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="784ab-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="784ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="784ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="784ab-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="784ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="784ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="784ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="784ab-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="784ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="784ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="784ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="784ab-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="784ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="784ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="784ab-120">E_FAIL</span></span>|<span data-ttu-id="784ab-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="784ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="784ab-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="784ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="784ab-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="784ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="784ab-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="784ab-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="784ab-125">Nedostatek paměti nebyly k dispozici k vytvoření požadované kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="784ab-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="784ab-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="784ab-126">Remarks</span></span>  
 <span data-ttu-id="784ab-127">Kritická sekce objekty poskytují synchronizace, který poskytuje objekt mutex podobný s tím rozdílem, že kritické oddíly mohou být používány pouze vláken v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="784ab-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> `CreateCrst` <span data-ttu-id="784ab-128">odráží Win32 `InitializeCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="784ab-128">mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="784ab-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="784ab-129">Requirements</span></span>  
 <span data-ttu-id="784ab-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="784ab-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="784ab-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="784ab-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="784ab-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="784ab-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="784ab-133">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="784ab-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="784ab-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="784ab-134">See also</span></span>

- [<span data-ttu-id="784ab-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="784ab-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="784ab-136">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="784ab-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="784ab-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="784ab-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="784ab-138">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="784ab-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="784ab-139">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="784ab-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)
- [<span data-ttu-id="784ab-140">Semafor a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="784ab-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
