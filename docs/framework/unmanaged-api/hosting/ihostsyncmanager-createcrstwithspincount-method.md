---
title: IHostSyncManager::CreateCrstWithSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139409"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="3724a-102">IHostSyncManager::CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="3724a-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="3724a-103">Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="3724a-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3724a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3724a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3724a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3724a-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="3724a-106">pro Určuje počet číselníků pro objekt kritické sekce.</span><span class="sxs-lookup"><span data-stu-id="3724a-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="3724a-107">mimo Ukazatel na adresu instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) nebo hodnotu null, pokud nelze vytvořit oddíl Critical.</span><span class="sxs-lookup"><span data-stu-id="3724a-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3724a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3724a-108">Return Value</span></span>  
  
|<span data-ttu-id="3724a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3724a-109">HRESULT</span></span>|<span data-ttu-id="3724a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="3724a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3724a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3724a-111">S_OK</span></span>|<span data-ttu-id="3724a-112">`CreateCrstWithSpinCount` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3724a-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="3724a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3724a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3724a-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3724a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3724a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3724a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3724a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3724a-116">The call timed out.</span></span>|  
|<span data-ttu-id="3724a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3724a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3724a-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3724a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3724a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3724a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3724a-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3724a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3724a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3724a-121">E_FAIL</span></span>|<span data-ttu-id="3724a-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3724a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3724a-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3724a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3724a-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3724a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3724a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3724a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3724a-126">Pro vytvoření požadovaného kritického oddílu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="3724a-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3724a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3724a-127">Remarks</span></span>  
 <span data-ttu-id="3724a-128">Počet číselníků se používá jenom v systému s více procesory.</span><span class="sxs-lookup"><span data-stu-id="3724a-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="3724a-129">Počet číselník určuje počet pokusů, které volající vlákno musí provést před tím, než provede operaci čekání na semaforu, který je přidružen k nedostupnému kritickému oddílu.</span><span class="sxs-lookup"><span data-stu-id="3724a-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="3724a-130">Pokud se kritická část uvolní během operace otáčení, volající vlákno se vyhne operaci čekání.</span><span class="sxs-lookup"><span data-stu-id="3724a-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="3724a-131">`CreateCrstWithSpinCount` zrcadlí funkci Win32 `InitializeCriticalSectionAndSpinCount`.</span><span class="sxs-lookup"><span data-stu-id="3724a-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3724a-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3724a-132">Requirements</span></span>  
 <span data-ttu-id="3724a-133">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3724a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3724a-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3724a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3724a-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3724a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3724a-136">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3724a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3724a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3724a-137">See also</span></span>

- [<span data-ttu-id="3724a-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3724a-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3724a-139">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3724a-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="3724a-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3724a-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
