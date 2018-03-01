---
title: "ICLROnEventManager::UnregisterActionOnEvent – metoda"
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
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d295817a7c6f8a177de3ff251904beeaf8ca828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="28db6-102">ICLROnEventManager::UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="28db6-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="28db6-103">Zruší registraci ukazatel dříve zaregistrovaný zpětného volání pro zadané události.</span><span class="sxs-lookup"><span data-stu-id="28db6-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28db6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28db6-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28db6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28db6-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="28db6-106">[v] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty, označující událostí, pro kterou chcete zrušit registraci zpětného volání ukazatele popsaného `pAction`.</span><span class="sxs-lookup"><span data-stu-id="28db6-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="28db6-107">[v] Ukazatel na [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objekt, který byl předán jako parametr, který se [registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="28db6-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28db6-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="28db6-108">Return Value</span></span>  
  
|<span data-ttu-id="28db6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="28db6-109">HRESULT</span></span>|<span data-ttu-id="28db6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="28db6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="28db6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="28db6-111">S_OK</span></span>|<span data-ttu-id="28db6-112">`UnregisterActionOnEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="28db6-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="28db6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="28db6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="28db6-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="28db6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="28db6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="28db6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="28db6-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="28db6-116">The call timed out.</span></span>|  
|<span data-ttu-id="28db6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="28db6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="28db6-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="28db6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="28db6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="28db6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="28db6-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="28db6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="28db6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="28db6-121">E_FAIL</span></span>|<span data-ttu-id="28db6-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="28db6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="28db6-123">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="28db6-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="28db6-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="28db6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28db6-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28db6-125">Requirements</span></span>  
 <span data-ttu-id="28db6-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28db6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28db6-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28db6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28db6-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28db6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28db6-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28db6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28db6-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="28db6-130">See Also</span></span>  
 [<span data-ttu-id="28db6-131">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="28db6-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="28db6-132">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28db6-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="28db6-133">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28db6-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="28db6-134">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="28db6-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
