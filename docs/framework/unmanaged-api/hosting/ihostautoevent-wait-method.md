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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7921f0361d7369cddf14dd1ab477529d1bbac481
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439358"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="e34ec-102">IHostAutoEvent::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="e34ec-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="e34ec-103">Způsobí, že aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="e34ec-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e34ec-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e34ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e34ec-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="e34ec-106">[v] Počet milisekund, po aktuální `IHostAutoEvent` instance čekat před vrácením, pokud žádný přístup z více vláken nebo fiber trvá vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="e34ec-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="e34ec-107">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, zadání akce hostitele provést v případě, že tato operace bloky.</span><span class="sxs-lookup"><span data-stu-id="e34ec-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e34ec-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e34ec-108">Return Value</span></span>  
  
|<span data-ttu-id="e34ec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e34ec-109">HRESULT</span></span>|<span data-ttu-id="e34ec-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e34ec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e34ec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e34ec-111">S_OK</span></span>|<span data-ttu-id="e34ec-112">`Wait` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e34ec-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="e34ec-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e34ec-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e34ec-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e34ec-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e34ec-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e34ec-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e34ec-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e34ec-116">The call timed out.</span></span>|  
|<span data-ttu-id="e34ec-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e34ec-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e34ec-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e34ec-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e34ec-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e34ec-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e34ec-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e34ec-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e34ec-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e34ec-121">E_FAIL</span></span>|<span data-ttu-id="e34ec-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e34ec-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e34ec-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e34ec-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e34ec-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e34ec-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e34ec-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="e34ec-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="e34ec-126">Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolili události, které aktuální `IHostAutoEvent` instance jako oběť vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="e34ec-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e34ec-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e34ec-127">Requirements</span></span>  
 <span data-ttu-id="e34ec-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e34ec-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e34ec-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e34ec-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e34ec-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e34ec-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e34ec-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e34ec-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34ec-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e34ec-132">See Also</span></span>  
 [<span data-ttu-id="e34ec-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e34ec-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e34ec-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e34ec-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e34ec-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e34ec-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e34ec-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e34ec-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
