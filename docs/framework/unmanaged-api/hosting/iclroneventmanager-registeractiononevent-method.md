---
title: "ICLROnEventManager::RegisterActionOnEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.RegisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ef99527abc7ca33e1176958a590483f34556a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="a56b3-102">ICLROnEventManager::RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="a56b3-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="a56b3-103">Zaregistruje zpětné volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="a56b3-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a56b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a56b3-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a56b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a56b3-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="a56b3-106">[v] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty, označující událostí, pro které chcete zaregistrovat zpětného volání ukazatele popsaného `pAction`.</span><span class="sxs-lookup"><span data-stu-id="a56b3-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="a56b3-107">[v] Ukazatel na [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objektu, která je volána, když se aktivuje registrované události.</span><span class="sxs-lookup"><span data-stu-id="a56b3-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a56b3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a56b3-108">Return Value</span></span>  
  
|<span data-ttu-id="a56b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a56b3-109">HRESULT</span></span>|<span data-ttu-id="a56b3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a56b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a56b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a56b3-111">S_OK</span></span>|<span data-ttu-id="a56b3-112">`RegisterActionOnEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a56b3-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a56b3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a56b3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a56b3-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a56b3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a56b3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a56b3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a56b3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a56b3-116">The call timed out.</span></span>|  
|<span data-ttu-id="a56b3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a56b3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a56b3-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a56b3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a56b3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a56b3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a56b3-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a56b3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a56b3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a56b3-121">E_FAIL</span></span>|<span data-ttu-id="a56b3-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a56b3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a56b3-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a56b3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a56b3-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a56b3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a56b3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a56b3-125">Remarks</span></span>  
 <span data-ttu-id="a56b3-126">Hostitel může registrace zpětných volání pro jednu nebo obě dvě události typy popsaného `EClrEvent`.</span><span class="sxs-lookup"><span data-stu-id="a56b3-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="a56b3-127">Získá hostitele `ICLROnEventManager` rozhraní voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a56b3-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a56b3-128">Události, `RegisterActionOnEvent` registry může být aktivována více než jednou a z různých vláknech signál uvolnění nebo zakázání modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a56b3-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a56b3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a56b3-129">Requirements</span></span>  
 <span data-ttu-id="a56b3-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a56b3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a56b3-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a56b3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a56b3-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a56b3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a56b3-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a56b3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56b3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a56b3-134">See Also</span></span>  
 [<span data-ttu-id="a56b3-135">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="a56b3-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="a56b3-136">Iactiononclrevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a56b3-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="a56b3-137">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a56b3-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a56b3-138">Iclroneventmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a56b3-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
