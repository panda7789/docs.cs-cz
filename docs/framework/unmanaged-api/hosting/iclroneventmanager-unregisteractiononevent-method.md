---
title: ICLROnEventManager::UnregisterActionOnEvent – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fcc5a6c2f2aa6f22a243c53898cdeda807b6774
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471809"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="6f6a3-102">ICLROnEventManager::UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="6f6a3-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="6f6a3-103">Zrušení registrace již registrovaného zpětného volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f6a3-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f6a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f6a3-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="6f6a3-106">[in] Jeden z [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty určující událost, pro které chcete zrušit registraci ukazatel zpětného volání popsal `pAction`.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="6f6a3-107">[in] Ukazatel na [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) objekt, který byl předán jako parametr, který se [registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f6a3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f6a3-108">Return Value</span></span>  
  
|<span data-ttu-id="6f6a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f6a3-109">HRESULT</span></span>|<span data-ttu-id="6f6a3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6f6a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f6a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f6a3-111">S_OK</span></span>|<span data-ttu-id="6f6a3-112">`UnregisterActionOnEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="6f6a3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6f6a3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6f6a3-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6f6a3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6f6a3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6f6a3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-116">The call timed out.</span></span>|  
|<span data-ttu-id="6f6a3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6f6a3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6f6a3-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6f6a3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6f6a3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6f6a3-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6f6a3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6f6a3-121">E_FAIL</span></span>|<span data-ttu-id="6f6a3-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6f6a3-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6f6a3-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6f6a3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f6a3-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f6a3-125">Requirements</span></span>  
 <span data-ttu-id="6f6a3-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f6a3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6a3-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f6a3-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f6a3-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f6a3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f6a3-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6a3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6a3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f6a3-130">See also</span></span>
- [<span data-ttu-id="6f6a3-131">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="6f6a3-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="6f6a3-132">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f6a3-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="6f6a3-133">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f6a3-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6f6a3-134">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f6a3-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
