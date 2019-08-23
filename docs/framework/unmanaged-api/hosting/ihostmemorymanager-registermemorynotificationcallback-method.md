---
title: IHostMemoryManager::RegisterMemoryNotificationCallback – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34701642a9e76ec52141e00fe9dde92878faccd2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945439"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="0421a-102">IHostMemoryManager::RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="0421a-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="0421a-103">Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil na modul CLR (Common Language Runtime) aktuálního zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="0421a-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0421a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0421a-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0421a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0421a-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="0421a-106">pro Ukazatel rozhraní na instanci [ICLRMemoryNotificationCallback –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) , která je implementována modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="0421a-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0421a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0421a-107">Return Value</span></span>  
  
|<span data-ttu-id="0421a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0421a-108">HRESULT</span></span>|<span data-ttu-id="0421a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0421a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0421a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0421a-110">S_OK</span></span>|<span data-ttu-id="0421a-111">`RegisterMemoryNotificationCallback`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0421a-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="0421a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0421a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0421a-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0421a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0421a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0421a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0421a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0421a-115">The call timed out.</span></span>|  
|<span data-ttu-id="0421a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0421a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0421a-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0421a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0421a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0421a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0421a-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0421a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0421a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0421a-120">E_FAIL</span></span>|<span data-ttu-id="0421a-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0421a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0421a-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0421a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0421a-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0421a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0421a-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0421a-124">Remarks</span></span>  
 <span data-ttu-id="0421a-125">Vzhledem k tomu, že `pCallback` `ICLRMemoryNotificationCallback` [](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) rozhranídefinujepouzejednumetodu(ICLRMemoryNotificationCallback–::OnMemoryNotification–)aprotožejeukazatelnainstanciposkytovanoumodulem`ICLRMemoryNotificationCallback` CLR, registrace je efektivně pro funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0421a-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="0421a-126">Hostitel vyvolá `OnMemoryNotification` hlášení stavů paměti místo použití standardní funkce Win32 `CreateMemoryResourceNotification` .</span><span class="sxs-lookup"><span data-stu-id="0421a-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="0421a-127">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="0421a-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0421a-128">`OnMemoryNotification` Volání nikdy neblokuje.</span><span class="sxs-lookup"><span data-stu-id="0421a-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="0421a-129">Vždycky se vrátí hned.</span><span class="sxs-lookup"><span data-stu-id="0421a-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0421a-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0421a-130">Requirements</span></span>  
 <span data-ttu-id="0421a-131">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0421a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0421a-132">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0421a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0421a-133">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0421a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0421a-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0421a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0421a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0421a-135">See also</span></span>

- [<span data-ttu-id="0421a-136">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0421a-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="0421a-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0421a-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
