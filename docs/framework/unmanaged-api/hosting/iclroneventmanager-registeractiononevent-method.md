---
title: ICLROnEventManager::RegisterActionOnEvent – metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68a8493a9eb5177844e81ef7a9612f979ffe89c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216493"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="392b3-102">ICLROnEventManager::RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="392b3-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="392b3-103">Zaregistruje zpětné volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="392b3-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="392b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="392b3-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="392b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="392b3-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="392b3-106">[in] Jeden z [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty určující událost, pro kterou se má registrovat zpětné volání ukazatel popsal `pAction`.</span><span class="sxs-lookup"><span data-stu-id="392b3-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="392b3-107">[in] Ukazatel [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objektu, která je volána, když se aktivuje registrované události.</span><span class="sxs-lookup"><span data-stu-id="392b3-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="392b3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="392b3-108">Return Value</span></span>  
  
|<span data-ttu-id="392b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="392b3-109">HRESULT</span></span>|<span data-ttu-id="392b3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="392b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="392b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="392b3-111">S_OK</span></span>|`RegisterActionOnEvent` <span data-ttu-id="392b3-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="392b3-112">returned successfully.</span></span>|  
|<span data-ttu-id="392b3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="392b3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="392b3-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="392b3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="392b3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="392b3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="392b3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="392b3-116">The call timed out.</span></span>|  
|<span data-ttu-id="392b3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="392b3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="392b3-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="392b3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="392b3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="392b3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="392b3-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="392b3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="392b3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="392b3-121">E_FAIL</span></span>|<span data-ttu-id="392b3-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="392b3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="392b3-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="392b3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="392b3-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="392b3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="392b3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="392b3-125">Remarks</span></span>  
 <span data-ttu-id="392b3-126">Hostitel může registrace zpětných volání pro jednu nebo obě dvě události typy popsal `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="392b3-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="392b3-127">Získá hostitele `ICLROnEventManager` rozhraní voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="392b3-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="392b3-128">Události, která `RegisterActionOnEvent` registrů můžete vyvoláno více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.</span><span class="sxs-lookup"><span data-stu-id="392b3-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="392b3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="392b3-129">Requirements</span></span>  
 <span data-ttu-id="392b3-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="392b3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="392b3-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="392b3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="392b3-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="392b3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="392b3-133">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="392b3-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="392b3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="392b3-134">See also</span></span>

- [<span data-ttu-id="392b3-135">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="392b3-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="392b3-136">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="392b3-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="392b3-137">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="392b3-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="392b3-138">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="392b3-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
