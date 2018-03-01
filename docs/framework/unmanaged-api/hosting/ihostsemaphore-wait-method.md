---
title: "IHostSemaphore::Wait – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15c86ee8b1de22f07b01290f5a830afd95427ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="11862-102">IHostSemaphore::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="11862-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="11862-103">Způsobí, že aktuální [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="11862-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11862-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11862-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11862-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="11862-106">[v] Počet milisekund čekání před návratem, pokud aktuální `IHostSemaphore` instance není ve vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="11862-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="11862-107">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, které určíte, co hostitele provést v případě, že tato operace bloky.</span><span class="sxs-lookup"><span data-stu-id="11862-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11862-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="11862-108">Return Value</span></span>  
  
|<span data-ttu-id="11862-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11862-109">HRESULT</span></span>|<span data-ttu-id="11862-110">Popis</span><span class="sxs-lookup"><span data-stu-id="11862-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11862-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="11862-111">S_OK</span></span>|<span data-ttu-id="11862-112">`Wait`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="11862-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="11862-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11862-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11862-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="11862-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11862-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11862-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11862-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="11862-116">The call timed out.</span></span>|  
|<span data-ttu-id="11862-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11862-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11862-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="11862-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11862-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11862-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11862-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="11862-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11862-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11862-121">E_FAIL</span></span>|<span data-ttu-id="11862-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="11862-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11862-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="11862-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11862-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="11862-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="11862-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="11862-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="11862-126">Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolili aktuální `IHostSemaphore` instance jako oběť vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="11862-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11862-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11862-127">Requirements</span></span>  
 <span data-ttu-id="11862-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11862-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11862-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="11862-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11862-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11862-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11862-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11862-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11862-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="11862-132">See Also</span></span>  
 [<span data-ttu-id="11862-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11862-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="11862-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11862-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="11862-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11862-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="11862-136">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11862-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="11862-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11862-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
