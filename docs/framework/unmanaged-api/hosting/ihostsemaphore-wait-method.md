---
title: IHostSemaphore::Wait – metoda
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 22d570711c293dd8c0cc6fefd198dd46d6489bea
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803538"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="0e8e2-102">IHostSemaphore::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="0e8e2-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="0e8e2-103">Způsobí, že aktuální instance [IHostSemaphore](ihostsemaphore-interface.md) počká, až bude ve vlastnictví, nebo zadanou dobu uplyne.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e8e2-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e8e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e8e2-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="0e8e2-106">pro Počet milisekund, po které se má čekat před vrácením, pokud aktuální `IHostSemaphore` instance není vlastněná.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="0e8e2-107">pro Jedna z hodnot [WAIT_OPTION](wait-option-enumeration.md) určuje, jakou akci by měl hostitel provést, pokud tato operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e8e2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0e8e2-108">Return Value</span></span>  
  
|<span data-ttu-id="0e8e2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e8e2-109">HRESULT</span></span>|<span data-ttu-id="0e8e2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0e8e2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e8e2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e8e2-111">S_OK</span></span>|<span data-ttu-id="0e8e2-112">`Wait`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="0e8e2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e8e2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e8e2-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e8e2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e8e2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e8e2-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-116">The call timed out.</span></span>|  
|<span data-ttu-id="0e8e2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e8e2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e8e2-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e8e2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e8e2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e8e2-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e8e2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e8e2-121">E_FAIL</span></span>|<span data-ttu-id="0e8e2-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e8e2-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e8e2-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0e8e2-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="0e8e2-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="0e8e2-126">Hostitel zjistil zablokování během intervalu čekání a `IHostSemaphore` jako oběť zablokování zvolí aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="0e8e2-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e8e2-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e8e2-127">Requirements</span></span>  
 <span data-ttu-id="0e8e2-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e8e2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e8e2-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e8e2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e8e2-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e8e2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e8e2-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e8e2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8e2-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e8e2-132">See also</span></span>

- [<span data-ttu-id="0e8e2-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8e2-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0e8e2-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8e2-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="0e8e2-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8e2-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="0e8e2-136">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8e2-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="0e8e2-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e8e2-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
