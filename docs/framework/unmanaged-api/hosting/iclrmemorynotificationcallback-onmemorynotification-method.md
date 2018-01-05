---
title: "ICLRMemoryNotificationCallback::OnMemoryNotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651dcd6380702a392d2dd06cf899ea567b004ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="34eb1-102">ICLRMemoryNotificationCallback::OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="34eb1-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="34eb1-103">Modul CLR (CLR) upozorní zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="34eb1-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34eb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34eb1-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34eb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34eb1-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="34eb1-106">[v] Jeden z [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) hodnoty, označující přetížení paměti počítači se aktuálně vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="34eb1-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34eb1-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="34eb1-107">Return Value</span></span>  
  
|<span data-ttu-id="34eb1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34eb1-108">HRESULT</span></span>|<span data-ttu-id="34eb1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="34eb1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34eb1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34eb1-110">S_OK</span></span>|<span data-ttu-id="34eb1-111">`OnMemoryNotification`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="34eb1-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="34eb1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="34eb1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="34eb1-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="34eb1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="34eb1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="34eb1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="34eb1-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="34eb1-115">The call timed out.</span></span>|  
|<span data-ttu-id="34eb1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="34eb1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="34eb1-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="34eb1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="34eb1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="34eb1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="34eb1-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="34eb1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="34eb1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34eb1-120">E_FAIL</span></span>|<span data-ttu-id="34eb1-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="34eb1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34eb1-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="34eb1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="34eb1-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34eb1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34eb1-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34eb1-124">Remarks</span></span>  
 <span data-ttu-id="34eb1-125">Modul CLR zaregistruje zpětné volání pro `OnMemoryNotification` pomocí volání [ihostmemorymanager::registermemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="34eb1-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="34eb1-126">Modul runtime používá vrácené v zpětné volání informace uvolnit více paměti, když hostitel ohlásí, že prostředky jsou spuštěné nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="34eb1-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34eb1-127">Volání `OnMemoryNotification` nikdy blokovat.</span><span class="sxs-lookup"><span data-stu-id="34eb1-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="34eb1-128">Vždy vracejí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="34eb1-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34eb1-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34eb1-129">Requirements</span></span>  
 <span data-ttu-id="34eb1-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34eb1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34eb1-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34eb1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34eb1-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34eb1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34eb1-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34eb1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34eb1-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="34eb1-134">See Also</span></span>  
 [<span data-ttu-id="34eb1-135">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34eb1-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="34eb1-136">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="34eb1-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="34eb1-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34eb1-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
