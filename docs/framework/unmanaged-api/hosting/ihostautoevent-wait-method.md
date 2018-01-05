---
title: "IHostAutoEvent::Wait – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4646e0bd04d69e7fe0125740c9c6e0c1b014071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="33ab6-102">IHostAutoEvent::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="33ab6-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="33ab6-103">Způsobí, že aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="33ab6-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33ab6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33ab6-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33ab6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33ab6-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="33ab6-106">[v] Počet milisekund, po aktuální `IHostAutoEvent` instance čekat před vrácením, pokud žádný přístup z více vláken nebo fiber trvá vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="33ab6-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="33ab6-107">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, zadání akce hostitele provést v případě, že tato operace bloky.</span><span class="sxs-lookup"><span data-stu-id="33ab6-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33ab6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="33ab6-108">Return Value</span></span>  
  
|<span data-ttu-id="33ab6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33ab6-109">HRESULT</span></span>|<span data-ttu-id="33ab6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="33ab6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33ab6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="33ab6-111">S_OK</span></span>|<span data-ttu-id="33ab6-112">`Wait`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="33ab6-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="33ab6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33ab6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33ab6-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="33ab6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33ab6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33ab6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33ab6-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="33ab6-116">The call timed out.</span></span>|  
|<span data-ttu-id="33ab6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33ab6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33ab6-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="33ab6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33ab6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33ab6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33ab6-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="33ab6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33ab6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33ab6-121">E_FAIL</span></span>|<span data-ttu-id="33ab6-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="33ab6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33ab6-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="33ab6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33ab6-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="33ab6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="33ab6-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="33ab6-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="33ab6-126">Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolili události, které aktuální `IHostAutoEvent` instance jako oběť vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="33ab6-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33ab6-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33ab6-127">Requirements</span></span>  
 <span data-ttu-id="33ab6-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ab6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ab6-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33ab6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33ab6-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33ab6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33ab6-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ab6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ab6-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="33ab6-132">See Also</span></span>  
 [<span data-ttu-id="33ab6-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33ab6-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="33ab6-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33ab6-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="33ab6-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33ab6-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="33ab6-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33ab6-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
