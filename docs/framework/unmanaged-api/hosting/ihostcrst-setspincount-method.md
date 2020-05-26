---
title: IHostCrst::SetSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804873"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="f356b-102">IHostCrst::SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="f356b-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="f356b-103">Nastaví počet číselníků pro aktuální instanci [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f356b-103">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f356b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f356b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f356b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f356b-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="f356b-106">pro Nový počet číselníků pro aktuální `IHostCrst` instanci.</span><span class="sxs-lookup"><span data-stu-id="f356b-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f356b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f356b-107">Return Value</span></span>  
  
|<span data-ttu-id="f356b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f356b-108">HRESULT</span></span>|<span data-ttu-id="f356b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f356b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f356b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f356b-110">S_OK</span></span>|<span data-ttu-id="f356b-111">`SetSpinCount`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f356b-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="f356b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f356b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f356b-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f356b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f356b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f356b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f356b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f356b-115">The call timed out.</span></span>|  
|<span data-ttu-id="f356b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f356b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f356b-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f356b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f356b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f356b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f356b-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f356b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f356b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f356b-120">E_FAIL</span></span>|<span data-ttu-id="f356b-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f356b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f356b-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f356b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f356b-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f356b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f356b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f356b-124">Remarks</span></span>  
 <span data-ttu-id="f356b-125">U systémů s více procesory platí, že pokud je kritická část reprezentovaná aktuální `IHostCrst` instancí nedostupná, volající vlákno se `dwSpinCount` před voláním [IHostSemaphore:: vyčká](ihostsemaphore-wait-method.md) na semaforu přidruženého k důležité části.</span><span class="sxs-lookup"><span data-stu-id="f356b-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="f356b-126">Pokud se kritická část uvolní během operace otáčení, volající vlákno se vyhne operaci čekání.</span><span class="sxs-lookup"><span data-stu-id="f356b-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="f356b-127">Použití `dwSpinCount` je stejné jako použití parametru se stejným názvem ve `InitializeCriticalSectionAndSpinCount` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="f356b-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f356b-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f356b-128">Requirements</span></span>  
 <span data-ttu-id="f356b-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f356b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f356b-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f356b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f356b-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f356b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f356b-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f356b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f356b-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f356b-133">See also</span></span>

- [<span data-ttu-id="f356b-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f356b-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f356b-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f356b-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="f356b-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f356b-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
