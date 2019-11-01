---
title: IHostAutoEvent::Wait – metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 0258999bae8b04ddaccf264276d1439b027b4a43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195893"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="019ef-102">IHostAutoEvent::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="019ef-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="019ef-103">Způsobí, že aktuální instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) počká, dokud se nevlastní nebo dokud neuplyne zadaný čas.</span><span class="sxs-lookup"><span data-stu-id="019ef-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="019ef-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="019ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="019ef-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="019ef-106">pro Počet milisekund, po které má aktuální instance `IHostAutoEvent` před vrácením čekat, pokud žádné vlákno nebo vlákno nepřebírají vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="019ef-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="019ef-107">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) určující akci, kterou by měl hostitel provést, pokud tato operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="019ef-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="019ef-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="019ef-108">Return Value</span></span>  
  
|<span data-ttu-id="019ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="019ef-109">HRESULT</span></span>|<span data-ttu-id="019ef-110">Popis</span><span class="sxs-lookup"><span data-stu-id="019ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="019ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="019ef-111">S_OK</span></span>|<span data-ttu-id="019ef-112">`Wait` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="019ef-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="019ef-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="019ef-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="019ef-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="019ef-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="019ef-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="019ef-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="019ef-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="019ef-116">The call timed out.</span></span>|  
|<span data-ttu-id="019ef-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="019ef-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="019ef-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="019ef-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="019ef-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="019ef-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="019ef-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="019ef-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="019ef-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="019ef-121">E_FAIL</span></span>|<span data-ttu-id="019ef-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="019ef-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="019ef-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="019ef-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="019ef-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="019ef-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="019ef-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="019ef-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="019ef-126">Hostitel zjistil zablokování během intervalu čekání a jako oběť zablokování vybere událost reprezentovanou aktuální instancí `IHostAutoEvent`.</span><span class="sxs-lookup"><span data-stu-id="019ef-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="019ef-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="019ef-127">Requirements</span></span>  
 <span data-ttu-id="019ef-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="019ef-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="019ef-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="019ef-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="019ef-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="019ef-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="019ef-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="019ef-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019ef-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="019ef-132">See also</span></span>

- [<span data-ttu-id="019ef-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="019ef-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="019ef-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="019ef-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="019ef-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="019ef-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="019ef-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="019ef-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
