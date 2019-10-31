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
ms.openlocfilehash: 4068166438c524ad1c0ed4efe455b1f66b6641d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140837"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="ddcaf-102">ICLROnEventManager::RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="ddcaf-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="ddcaf-103">Zaregistruje ukazatel zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddcaf-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddcaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddcaf-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="ddcaf-106">pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje událost, pro kterou má být zaregistrován ukazatel zpětného volání popsaný `pAction`.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="ddcaf-107">pro Ukazatel na objekt [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , který se volá, když se aktivuje registrovaná událost.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddcaf-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddcaf-108">Return Value</span></span>  
  
|<span data-ttu-id="ddcaf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ddcaf-109">HRESULT</span></span>|<span data-ttu-id="ddcaf-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ddcaf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddcaf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddcaf-111">S_OK</span></span>|<span data-ttu-id="ddcaf-112">`RegisterActionOnEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="ddcaf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ddcaf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ddcaf-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ddcaf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ddcaf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ddcaf-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-116">The call timed out.</span></span>|  
|<span data-ttu-id="ddcaf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddcaf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ddcaf-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ddcaf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ddcaf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ddcaf-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ddcaf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ddcaf-121">E_FAIL</span></span>|<span data-ttu-id="ddcaf-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ddcaf-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ddcaf-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddcaf-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddcaf-125">Remarks</span></span>  
 <span data-ttu-id="ddcaf-126">Hostitel může zaregistrovat zpětná volání pro buď nebo oba typy událostí popsané `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="ddcaf-127">Hostitel získá rozhraní `ICLROnEventManager` voláním metody [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ddcaf-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddcaf-128">Události, které `RegisterActionOnEvent` Registry, lze aktivovat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.</span><span class="sxs-lookup"><span data-stu-id="ddcaf-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcaf-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddcaf-129">Requirements</span></span>  
 <span data-ttu-id="ddcaf-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddcaf-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddcaf-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ddcaf-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ddcaf-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ddcaf-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddcaf-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddcaf-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcaf-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddcaf-134">See also</span></span>

- [<span data-ttu-id="ddcaf-135">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="ddcaf-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="ddcaf-136">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddcaf-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="ddcaf-137">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddcaf-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="ddcaf-138">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddcaf-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
