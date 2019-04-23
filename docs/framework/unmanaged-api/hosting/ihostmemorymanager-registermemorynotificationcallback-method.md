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
ms.openlocfilehash: 87dfbe85d279aa191253857887c1d9b5b5f8c7cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088519"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="8931d-102">IHostMemoryManager::RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="8931d-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="8931d-103">Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele upozornit modul CLR (CLR) z aktuálního zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="8931d-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8931d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8931d-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8931d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8931d-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="8931d-106">[in] Ukazatel rozhraní k [iclrmemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instanci, která je implementováno modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="8931d-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8931d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8931d-107">Return Value</span></span>  
  
|<span data-ttu-id="8931d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8931d-108">HRESULT</span></span>|<span data-ttu-id="8931d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8931d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8931d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8931d-110">S_OK</span></span>|<span data-ttu-id="8931d-111">`RegisterMemoryNotificationCallback` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8931d-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="8931d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8931d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8931d-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8931d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8931d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8931d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8931d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8931d-115">The call timed out.</span></span>|  
|<span data-ttu-id="8931d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8931d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8931d-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8931d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8931d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8931d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8931d-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8931d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8931d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8931d-120">E_FAIL</span></span>|<span data-ttu-id="8931d-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8931d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8931d-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8931d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8931d-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8931d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8931d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8931d-124">Remarks</span></span>  
 <span data-ttu-id="8931d-125">Protože `ICLRMemoryNotificationCallback` rozhraní definuje pouze jednu metodu ([iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na `ICLRMemoryNotificationCallback` zadaná pomocí modulu CLR, instance Registrace je v podstatě pro samotné funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8931d-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="8931d-126">Vyvolá hostitele `OnMemoryNotification` podmínky přetížení paměti sestavy, místo používání standardním Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="8931d-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="8931d-127">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="8931d-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8931d-128">Volání `OnMemoryNotification` není nikdy blokována.</span><span class="sxs-lookup"><span data-stu-id="8931d-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="8931d-129">Vždy vrátí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="8931d-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8931d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8931d-130">Requirements</span></span>  
 <span data-ttu-id="8931d-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8931d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8931d-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8931d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8931d-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8931d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8931d-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8931d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8931d-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8931d-135">See also</span></span>

- [<span data-ttu-id="8931d-136">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8931d-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="8931d-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8931d-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
