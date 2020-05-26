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
ms.openlocfilehash: 86bc320c28a5fbf122d234a4a1f15b674628c0b5
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803400"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="7ebb4-102">IHostSyncManager::CreateCrstWithSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7ebb4-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="7ebb4-103">Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ebb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ebb4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ebb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ebb4-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="7ebb4-106">pro Určuje počet číselníků pro objekt kritické sekce.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="7ebb4-107">mimo Ukazatel na adresu instance [IHostCrst](ihostcrst-interface.md) nebo hodnotu null, pokud nelze vytvořit oddíl Critical.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ebb4-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ebb4-108">Return Value</span></span>  
  
|<span data-ttu-id="7ebb4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ebb4-109">HRESULT</span></span>|<span data-ttu-id="7ebb4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7ebb4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ebb4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ebb4-111">S_OK</span></span>|<span data-ttu-id="7ebb4-112">`CreateCrstWithSpinCount`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="7ebb4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ebb4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ebb4-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ebb4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ebb4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ebb4-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-116">The call timed out.</span></span>|  
|<span data-ttu-id="7ebb4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ebb4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ebb4-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ebb4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ebb4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ebb4-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ebb4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ebb4-121">E_FAIL</span></span>|<span data-ttu-id="7ebb4-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ebb4-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ebb4-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7ebb4-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7ebb4-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7ebb4-126">Pro vytvoření požadovaného kritického oddílu není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ebb4-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ebb4-127">Remarks</span></span>  
 <span data-ttu-id="7ebb4-128">Počet číselníků se používá jenom v systému s více procesory.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="7ebb4-129">Počet číselník určuje počet pokusů, které volající vlákno musí provést před tím, než provede operaci čekání na semaforu, který je přidružen k nedostupnému kritickému oddílu.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="7ebb4-130">Pokud se kritická část uvolní během operace otáčení, volající vlákno se vyhne operaci čekání.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="7ebb4-131">`CreateCrstWithSpinCount`zrcadlí `InitializeCriticalSectionAndSpinCount` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="7ebb4-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ebb4-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ebb4-132">Requirements</span></span>  
 <span data-ttu-id="7ebb4-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ebb4-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ebb4-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7ebb4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ebb4-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7ebb4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ebb4-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ebb4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ebb4-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ebb4-137">See also</span></span>

- [<span data-ttu-id="7ebb4-138">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ebb4-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7ebb4-139">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ebb4-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="7ebb4-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ebb4-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
