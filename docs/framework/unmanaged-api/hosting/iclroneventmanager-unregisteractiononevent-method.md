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
ms.openlocfilehash: 0f952978a2591c82b2ad3f5059070124b7873c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140822"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="70c70-102">ICLROnEventManager::UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="70c70-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="70c70-103">Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="70c70-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70c70-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70c70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70c70-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="70c70-106">pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje událost, pro kterou má být odregistrován ukazatel zpětného volání popsaný `pAction`.</span><span class="sxs-lookup"><span data-stu-id="70c70-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="70c70-107">pro Ukazatel na objekt [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , který byl předán jako parametr metodě [RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="70c70-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70c70-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70c70-108">Return Value</span></span>  
  
|<span data-ttu-id="70c70-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70c70-109">HRESULT</span></span>|<span data-ttu-id="70c70-110">Popis</span><span class="sxs-lookup"><span data-stu-id="70c70-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70c70-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="70c70-111">S_OK</span></span>|<span data-ttu-id="70c70-112">`UnregisterActionOnEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="70c70-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="70c70-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70c70-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70c70-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="70c70-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70c70-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70c70-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70c70-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="70c70-116">The call timed out.</span></span>|  
|<span data-ttu-id="70c70-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70c70-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70c70-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="70c70-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70c70-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70c70-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70c70-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="70c70-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70c70-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70c70-121">E_FAIL</span></span>|<span data-ttu-id="70c70-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="70c70-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70c70-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="70c70-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70c70-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70c70-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70c70-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70c70-125">Requirements</span></span>  
 <span data-ttu-id="70c70-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70c70-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c70-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70c70-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70c70-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70c70-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70c70-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c70-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c70-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70c70-130">See also</span></span>

- [<span data-ttu-id="70c70-131">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="70c70-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="70c70-132">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70c70-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="70c70-133">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70c70-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="70c70-134">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70c70-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
