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
ms.openlocfilehash: bf09f7bc6c3e3aabfc16f9cad277c46be024b01d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139449"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="40fd6-102">IHostSemaphore::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="40fd6-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="40fd6-103">Způsobí, že aktuální instance [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) počká, až bude ve vlastnictví, nebo zadanou dobu uplyne.</span><span class="sxs-lookup"><span data-stu-id="40fd6-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40fd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40fd6-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40fd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40fd6-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="40fd6-106">pro Počet milisekund čekání před vrácením, pokud aktuální instance `IHostSemaphore` není vlastněná.</span><span class="sxs-lookup"><span data-stu-id="40fd6-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="40fd6-107">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , která určuje, jakou akci by měl hostitel provést, pokud tato operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="40fd6-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40fd6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="40fd6-108">Return Value</span></span>  
  
|<span data-ttu-id="40fd6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40fd6-109">HRESULT</span></span>|<span data-ttu-id="40fd6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="40fd6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40fd6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="40fd6-111">S_OK</span></span>|<span data-ttu-id="40fd6-112">`Wait` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="40fd6-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="40fd6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40fd6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40fd6-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="40fd6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40fd6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40fd6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40fd6-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="40fd6-116">The call timed out.</span></span>|  
|<span data-ttu-id="40fd6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40fd6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40fd6-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="40fd6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40fd6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40fd6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40fd6-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="40fd6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40fd6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40fd6-121">E_FAIL</span></span>|<span data-ttu-id="40fd6-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="40fd6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40fd6-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="40fd6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40fd6-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="40fd6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="40fd6-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="40fd6-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="40fd6-126">Hostitel zjistil zablokování během intervalu čekání a jako oběť zablokování zvolí aktuální `IHostSemaphore` instanci.</span><span class="sxs-lookup"><span data-stu-id="40fd6-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40fd6-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40fd6-127">Requirements</span></span>  
 <span data-ttu-id="40fd6-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40fd6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40fd6-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40fd6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40fd6-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40fd6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40fd6-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40fd6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fd6-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40fd6-132">See also</span></span>

- [<span data-ttu-id="40fd6-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40fd6-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="40fd6-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40fd6-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="40fd6-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40fd6-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="40fd6-136">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40fd6-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="40fd6-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40fd6-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
