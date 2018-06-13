---
title: ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 187c0a8d929958b7eaf1e99771da6a0d29c3d5f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434184"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="e1bf8-102">ICLRMemoryNotificationCallback::OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="e1bf8-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="e1bf8-103">Modul CLR (CLR) upozorní zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bf8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1bf8-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1bf8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1bf8-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="e1bf8-106">[v] Jeden z [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) hodnoty, označující přetížení paměti počítači se aktuálně vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1bf8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e1bf8-107">Return Value</span></span>  
  
|<span data-ttu-id="e1bf8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1bf8-108">HRESULT</span></span>|<span data-ttu-id="e1bf8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e1bf8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1bf8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1bf8-110">S_OK</span></span>|<span data-ttu-id="e1bf8-111">`OnMemoryNotification` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="e1bf8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e1bf8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e1bf8-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e1bf8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e1bf8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e1bf8-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-115">The call timed out.</span></span>|  
|<span data-ttu-id="e1bf8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e1bf8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e1bf8-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e1bf8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e1bf8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e1bf8-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e1bf8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1bf8-120">E_FAIL</span></span>|<span data-ttu-id="e1bf8-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e1bf8-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e1bf8-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1bf8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1bf8-124">Remarks</span></span>  
 <span data-ttu-id="e1bf8-125">Modul CLR zaregistruje zpětné volání pro `OnMemoryNotification` pomocí volání [ihostmemorymanager::registermemorynotificationcallback –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="e1bf8-126">Modul runtime používá vrácené v zpětné volání informace uvolnit více paměti, když hostitel ohlásí, že prostředky jsou spuštěné nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1bf8-127">Volání `OnMemoryNotification` nikdy blokovat.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="e1bf8-128">Vždy vracejí okamžitě.</span><span class="sxs-lookup"><span data-stu-id="e1bf8-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1bf8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1bf8-129">Requirements</span></span>  
 <span data-ttu-id="e1bf8-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1bf8-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1bf8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1bf8-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1bf8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1bf8-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1bf8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1bf8-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1bf8-134">See Also</span></span>  
 [<span data-ttu-id="e1bf8-135">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1bf8-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="e1bf8-136">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="e1bf8-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="e1bf8-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1bf8-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
