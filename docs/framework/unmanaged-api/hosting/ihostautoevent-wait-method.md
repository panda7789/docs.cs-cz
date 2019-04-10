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
ms.openlocfilehash: 3b07b3649cc1d7fcc2c75cbbd59414ee67819103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217923"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="0e6ac-102">IHostAutoEvent::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="0e6ac-102">IHostAutoEvent::Wait Method</span></span>
<span data-ttu-id="0e6ac-103">Způsobí, že aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance počkat, dokud je ve vlastnictví nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-103">Causes the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e6ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e6ac-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e6ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e6ac-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="0e6ac-106">[in] Počet milisekund aktuální `IHostAutoEvent` instance čekat před vrácením, pokud žádné vlákno nebo vlákno trvá vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-106">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="0e6ac-107">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnot určujících akce hostitele by neměl zabrat tato operace bloky.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e6ac-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0e6ac-108">Return Value</span></span>  
  
|<span data-ttu-id="0e6ac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e6ac-109">HRESULT</span></span>|<span data-ttu-id="0e6ac-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0e6ac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e6ac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e6ac-111">S_OK</span></span>|`Wait` <span data-ttu-id="0e6ac-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-112">returned successfully.</span></span>|  
|<span data-ttu-id="0e6ac-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e6ac-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e6ac-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e6ac-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e6ac-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e6ac-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-116">The call timed out.</span></span>|  
|<span data-ttu-id="0e6ac-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e6ac-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e6ac-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e6ac-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e6ac-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e6ac-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e6ac-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e6ac-121">E_FAIL</span></span>|<span data-ttu-id="0e6ac-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e6ac-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e6ac-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0e6ac-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="0e6ac-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="0e6ac-126">Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolit seskupování událostí reprezentované aktuální `IHostAutoEvent` instance jako oběť zablokování.</span><span class="sxs-lookup"><span data-stu-id="0e6ac-126">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e6ac-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e6ac-127">Requirements</span></span>  
 <span data-ttu-id="0e6ac-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e6ac-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e6ac-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e6ac-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e6ac-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e6ac-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0e6ac-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0e6ac-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e6ac-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e6ac-132">See also</span></span>

- [<span data-ttu-id="0e6ac-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e6ac-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0e6ac-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e6ac-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="0e6ac-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e6ac-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="0e6ac-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e6ac-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
