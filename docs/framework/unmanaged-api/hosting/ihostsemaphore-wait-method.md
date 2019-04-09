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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d9fcbca92b1615679be57fb4c9b872339fef8a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118212"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="8c6ce-102">IHostSemaphore::Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="8c6ce-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="8c6ce-103">Způsobí, že aktuální [ihostsemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance počkat, dokud je ve vlastnictví nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6ce-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c6ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c6ce-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="8c6ce-106">[in] Počet milisekund čekání před návratem, pokud aktuální `IHostSemaphore` instance není ve vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="8c6ce-107">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, určíte, co hostitel zabere tato operace bloky.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c6ce-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c6ce-108">Return Value</span></span>  
  
|<span data-ttu-id="8c6ce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c6ce-109">HRESULT</span></span>|<span data-ttu-id="8c6ce-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8c6ce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c6ce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c6ce-111">S_OK</span></span>|`Wait` <span data-ttu-id="8c6ce-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-112">returned successfully.</span></span>|  
|<span data-ttu-id="8c6ce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c6ce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c6ce-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c6ce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c6ce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c6ce-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-116">The call timed out.</span></span>|  
|<span data-ttu-id="8c6ce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c6ce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c6ce-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c6ce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c6ce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c6ce-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c6ce-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c6ce-121">E_FAIL</span></span>|<span data-ttu-id="8c6ce-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c6ce-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c6ce-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c6ce-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="8c6ce-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="8c6ce-126">Hostitel zjistil vzájemné zablokování během intervalu čekání a zvolili aktuální `IHostSemaphore` instance jako postižená transakce zablokování.</span><span class="sxs-lookup"><span data-stu-id="8c6ce-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c6ce-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c6ce-127">Requirements</span></span>  
 <span data-ttu-id="8c6ce-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6ce-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6ce-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c6ce-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c6ce-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c6ce-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8c6ce-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8c6ce-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c6ce-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c6ce-132">See also</span></span>

- [<span data-ttu-id="8c6ce-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ce-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8c6ce-134">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ce-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="8c6ce-135">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ce-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="8c6ce-136">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ce-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8c6ce-137">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c6ce-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
