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
ms.openlocfilehash: 8a9fdcd650e18bb91e2a4e30e5a22fb2a991d25c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703492"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="5d2c3-102">ICLROnEventManager::UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="5d2c3-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="5d2c3-103">Zruší registraci dříve registrovaného ukazatele zpětného volání pro zadanou událost.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d2c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d2c3-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d2c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d2c3-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="5d2c3-106">pro Jedna z hodnot [EClrEvent –](eclrevent-enumeration.md) , která označuje událost, pro kterou má být odregistrován ukazatel zpětného volání popsaný v `pAction` .</span><span class="sxs-lookup"><span data-stu-id="5d2c3-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="5d2c3-107">pro Ukazatel na objekt [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) , který byl předán jako parametr metodě [RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5d2c3-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d2c3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d2c3-108">Return Value</span></span>  
  
|<span data-ttu-id="5d2c3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d2c3-109">HRESULT</span></span>|<span data-ttu-id="5d2c3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5d2c3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d2c3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d2c3-111">S_OK</span></span>|<span data-ttu-id="5d2c3-112">`UnregisterActionOnEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="5d2c3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d2c3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d2c3-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d2c3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d2c3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d2c3-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-116">The call timed out.</span></span>|  
|<span data-ttu-id="5d2c3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d2c3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d2c3-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d2c3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d2c3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d2c3-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d2c3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d2c3-121">E_FAIL</span></span>|<span data-ttu-id="5d2c3-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d2c3-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d2c3-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5d2c3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d2c3-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d2c3-125">Requirements</span></span>  
 <span data-ttu-id="5d2c3-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d2c3-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d2c3-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d2c3-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d2c3-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5d2c3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d2c3-129">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d2c3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d2c3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d2c3-130">See also</span></span>

- [<span data-ttu-id="5d2c3-131">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="5d2c3-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="5d2c3-132">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d2c3-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="5d2c3-133">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d2c3-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="5d2c3-134">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d2c3-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
