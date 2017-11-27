---
title: "IHostMemoryManager::RegisterMemoryNotificationCallback – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.RegisterMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 142fd6edba9a517f0d43db9d070a47ebeba8d313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="e971f-102">IHostMemoryManager::RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="e971f-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="e971f-103">Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele upozornit modul CLR (CLR) aktuální zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="e971f-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e971f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e971f-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e971f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e971f-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="e971f-106">[v] Ukazatele rozhraní k [iclrmemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instanci, která je implementováno modulem modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e971f-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e971f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e971f-107">Return Value</span></span>  
  
|<span data-ttu-id="e971f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e971f-108">HRESULT</span></span>|<span data-ttu-id="e971f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e971f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e971f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e971f-110">S_OK</span></span>|<span data-ttu-id="e971f-111">`RegisterMemoryNotificationCallback`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e971f-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="e971f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e971f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e971f-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e971f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e971f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e971f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e971f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e971f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e971f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e971f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e971f-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e971f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e971f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e971f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e971f-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e971f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e971f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e971f-120">E_FAIL</span></span>|<span data-ttu-id="e971f-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e971f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e971f-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e971f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e971f-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e971f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e971f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e971f-124">Remarks</span></span>  
 <span data-ttu-id="e971f-125">Protože `ICLRMemoryNotificationCallback` rozhraní definuje pouze jednu metodu ([iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na `ICLRMemoryNotificationCallback` instance poskytované modulu CLR, Registrace je efektivně pro samotné funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e971f-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="e971f-126">Vyvolá hostitele `OnMemoryNotification` do sestavy podmínky přetížení paměti, nikoli pomocí standardní Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="e971f-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="e971f-127">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="e971f-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e971f-128">Volání `OnMemoryNotification` nikdy blokovat.</span><span class="sxs-lookup"><span data-stu-id="e971f-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="e971f-129">Vždy vracejí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e971f-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e971f-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e971f-130">Requirements</span></span>  
 <span data-ttu-id="e971f-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e971f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e971f-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e971f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e971f-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e971f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e971f-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e971f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e971f-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e971f-135">See Also</span></span>  
 [<span data-ttu-id="e971f-136">Iclrmemorynotificationcallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e971f-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="e971f-137">Ihostmemorymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e971f-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
