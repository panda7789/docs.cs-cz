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
ms.openlocfilehash: 8e5a0af2d2f3db5b1d44def3af067bc1c3a9e1aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485288"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="333f7-102">IHostMemoryManager::RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="333f7-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="333f7-103">Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele upozornit modul CLR (CLR) z aktuálního zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="333f7-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="333f7-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="333f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="333f7-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="333f7-106">[in] Ukazatel rozhraní k [iclrmemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instanci, která je implementováno modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="333f7-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="333f7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="333f7-107">Return Value</span></span>  
  
|<span data-ttu-id="333f7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="333f7-108">HRESULT</span></span>|<span data-ttu-id="333f7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="333f7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="333f7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="333f7-110">S_OK</span></span>|<span data-ttu-id="333f7-111">`RegisterMemoryNotificationCallback` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="333f7-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="333f7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="333f7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="333f7-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="333f7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="333f7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="333f7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="333f7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="333f7-115">The call timed out.</span></span>|  
|<span data-ttu-id="333f7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="333f7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="333f7-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="333f7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="333f7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="333f7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="333f7-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="333f7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="333f7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="333f7-120">E_FAIL</span></span>|<span data-ttu-id="333f7-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="333f7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="333f7-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="333f7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="333f7-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="333f7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="333f7-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="333f7-124">Remarks</span></span>  
 <span data-ttu-id="333f7-125">Protože `ICLRMemoryNotificationCallback` rozhraní definuje pouze jednu metodu ([iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na `ICLRMemoryNotificationCallback` zadaná pomocí modulu CLR, instance Registrace je v podstatě pro samotné funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="333f7-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="333f7-126">Vyvolá hostitele `OnMemoryNotification` podmínky přetížení paměti sestavy, místo používání standardním Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="333f7-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="333f7-127">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="333f7-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="333f7-128">Volání `OnMemoryNotification` není nikdy blokována.</span><span class="sxs-lookup"><span data-stu-id="333f7-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="333f7-129">Vždy vrátí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="333f7-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333f7-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="333f7-130">Requirements</span></span>  
 <span data-ttu-id="333f7-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333f7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333f7-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="333f7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="333f7-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="333f7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="333f7-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333f7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333f7-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="333f7-135">See also</span></span>
- [<span data-ttu-id="333f7-136">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="333f7-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="333f7-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="333f7-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
