---
title: IHostGCManager::SuspensionStarting – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00322a75c4a15e42c89ff5a8680171a168a37613
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758695"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="f11aa-102">IHostGCManager::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="f11aa-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="f11aa-103">Upozorňuje hostitele, že modul CLR (CLR) je pozastavení provádění úkolů, k provedení uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f11aa-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11aa-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f11aa-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f11aa-105">Return Value</span></span>  
  
|<span data-ttu-id="f11aa-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f11aa-106">HRESULT</span></span>|<span data-ttu-id="f11aa-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f11aa-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f11aa-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f11aa-108">S_OK</span></span>|<span data-ttu-id="f11aa-109">`SuspensionStarting` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f11aa-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="f11aa-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f11aa-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f11aa-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f11aa-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f11aa-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f11aa-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f11aa-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f11aa-113">The call timed out.</span></span>|  
|<span data-ttu-id="f11aa-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f11aa-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f11aa-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f11aa-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f11aa-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f11aa-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f11aa-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f11aa-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f11aa-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f11aa-118">E_FAIL</span></span>|<span data-ttu-id="f11aa-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f11aa-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f11aa-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f11aa-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f11aa-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f11aa-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f11aa-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f11aa-122">Remarks</span></span>  
 <span data-ttu-id="f11aa-123">Volání CLR `SuspensionStarting` informovat hostitele, dochází k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f11aa-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f11aa-124">Není plánovanou zkoušku přeplánovat této úlohy.</span><span class="sxs-lookup"><span data-stu-id="f11aa-124">Do not reschedule this task.</span></span> <span data-ttu-id="f11aa-125">Hostitel musí plánovanou zkoušku přeplánovat úlohu při [threadisblockingforsuspension –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="f11aa-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11aa-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f11aa-126">Requirements</span></span>  
 <span data-ttu-id="f11aa-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f11aa-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11aa-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f11aa-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f11aa-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f11aa-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f11aa-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11aa-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11aa-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f11aa-131">See also</span></span>

- [<span data-ttu-id="f11aa-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11aa-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f11aa-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11aa-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f11aa-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11aa-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f11aa-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11aa-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f11aa-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11aa-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
