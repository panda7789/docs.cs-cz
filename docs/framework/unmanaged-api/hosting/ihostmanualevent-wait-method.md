---
title: IHostManualEvent::Wait – metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: f39a5af706ef49e3f6e4bd040d752e5698063b29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136750"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="8e009-102">IHostManualEvent::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="8e009-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="8e009-103">Způsobí, že aktuální instance [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) počká, až bude ve vlastnictví, nebo zadanou dobu uplyne.</span><span class="sxs-lookup"><span data-stu-id="8e009-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e009-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e009-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e009-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e009-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="8e009-106">pro Počet milisekund čekání před vrácením, pokud aktuální instance `IHostManualEvent` není vlastněná.</span><span class="sxs-lookup"><span data-stu-id="8e009-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="8e009-107">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) označující akci, kterou by měl hostitel provést, pokud tato operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="8e009-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e009-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8e009-108">Return Value</span></span>  
  
|<span data-ttu-id="8e009-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e009-109">HRESULT</span></span>|<span data-ttu-id="8e009-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8e009-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e009-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e009-111">S_OK</span></span>|<span data-ttu-id="8e009-112">`Wait` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8e009-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="8e009-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e009-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e009-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8e009-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8e009-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8e009-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8e009-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8e009-116">The call timed out.</span></span>|  
|<span data-ttu-id="8e009-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8e009-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8e009-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8e009-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8e009-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8e009-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8e009-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8e009-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8e009-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e009-121">E_FAIL</span></span>|<span data-ttu-id="8e009-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8e009-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8e009-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8e009-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8e009-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8e009-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8e009-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="8e009-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="8e009-126">Hostitel zjistil zablokování během intervalu čekání a jako oběť zablokování zvolí aktuální `IHostManualEvent` instanci.</span><span class="sxs-lookup"><span data-stu-id="8e009-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e009-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e009-127">Requirements</span></span>  
 <span data-ttu-id="8e009-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e009-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e009-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e009-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e009-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8e009-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e009-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e009-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e009-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e009-132">See also</span></span>

- [<span data-ttu-id="8e009-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e009-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8e009-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e009-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="8e009-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e009-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="8e009-136">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e009-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8e009-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e009-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
