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
ms.openlocfilehash: 36d4b0692b112a66fea3dd878c7054a083fb68ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951152"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="c42cc-102">ICLROnEventManager::RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="c42cc-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="c42cc-103">Zaregistruje ukazatel zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="c42cc-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c42cc-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c42cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c42cc-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="c42cc-106">pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje událost, pro kterou má být zaregistrován ukazatel zpětného volání `pAction`popsaný v.</span><span class="sxs-lookup"><span data-stu-id="c42cc-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="c42cc-107">pro Ukazatel na objekt [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , který se volá, když se aktivuje registrovaná událost.</span><span class="sxs-lookup"><span data-stu-id="c42cc-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c42cc-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c42cc-108">Return Value</span></span>  
  
|<span data-ttu-id="c42cc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c42cc-109">HRESULT</span></span>|<span data-ttu-id="c42cc-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c42cc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c42cc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c42cc-111">S_OK</span></span>|<span data-ttu-id="c42cc-112">`RegisterActionOnEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c42cc-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c42cc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c42cc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c42cc-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c42cc-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c42cc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c42cc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c42cc-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c42cc-116">The call timed out.</span></span>|  
|<span data-ttu-id="c42cc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c42cc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c42cc-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c42cc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c42cc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c42cc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c42cc-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c42cc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c42cc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c42cc-121">E_FAIL</span></span>|<span data-ttu-id="c42cc-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c42cc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c42cc-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c42cc-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c42cc-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c42cc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c42cc-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c42cc-125">Remarks</span></span>  
 <span data-ttu-id="c42cc-126">Hostitel může zaregistrovat zpětná volání pro buď nebo obojí z obou typů událostí popsaných `EClrEvent`v.</span><span class="sxs-lookup"><span data-stu-id="c42cc-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="c42cc-127">Hostitel získá `ICLROnEventManager` rozhraní voláním metody [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c42cc-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c42cc-128">Události, které `RegisterActionOnEvent` mohou být zaregistrovány, lze aktivovat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.</span><span class="sxs-lookup"><span data-stu-id="c42cc-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c42cc-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c42cc-129">Requirements</span></span>  
 <span data-ttu-id="c42cc-130">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c42cc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c42cc-131">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c42cc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c42cc-132">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c42cc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c42cc-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c42cc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42cc-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c42cc-134">See also</span></span>

- [<span data-ttu-id="c42cc-135">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="c42cc-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="c42cc-136">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c42cc-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="c42cc-137">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c42cc-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c42cc-138">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c42cc-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
