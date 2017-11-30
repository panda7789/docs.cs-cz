---
title: "IHostGCManager::SuspensionStarting – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c807a124570f38922509d27e52936b980e36fba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="78aa5-102">IHostGCManager::SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="78aa5-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="78aa5-103">Upozorní hostitele, modul CLR (CLR) je pozastavení provádění úlohy, musíte provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="78aa5-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78aa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78aa5-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="78aa5-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78aa5-105">Return Value</span></span>  
  
|<span data-ttu-id="78aa5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78aa5-106">HRESULT</span></span>|<span data-ttu-id="78aa5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="78aa5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78aa5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="78aa5-108">S_OK</span></span>|<span data-ttu-id="78aa5-109">`SuspensionStarting`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="78aa5-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="78aa5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78aa5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78aa5-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="78aa5-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78aa5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78aa5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78aa5-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="78aa5-113">The call timed out.</span></span>|  
|<span data-ttu-id="78aa5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78aa5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78aa5-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="78aa5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78aa5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78aa5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78aa5-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="78aa5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78aa5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78aa5-118">E_FAIL</span></span>|<span data-ttu-id="78aa5-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="78aa5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78aa5-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="78aa5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78aa5-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78aa5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78aa5-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78aa5-122">Remarks</span></span>  
 <span data-ttu-id="78aa5-123">Volání CLR `SuspensionStarting` k informování hostitele, který dochází k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="78aa5-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78aa5-124">Tato úloha nezměnila naplánování.</span><span class="sxs-lookup"><span data-stu-id="78aa5-124">Do not reschedule this task.</span></span> <span data-ttu-id="78aa5-125">Hostitel musí změnit plán naplánovaných úlohu při [threadisblockingforsuspension –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="78aa5-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78aa5-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78aa5-126">Requirements</span></span>  
 <span data-ttu-id="78aa5-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78aa5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78aa5-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78aa5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78aa5-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78aa5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78aa5-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78aa5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78aa5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="78aa5-131">See Also</span></span>  
 [<span data-ttu-id="78aa5-132">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78aa5-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="78aa5-133">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78aa5-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="78aa5-134">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78aa5-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="78aa5-135">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78aa5-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="78aa5-136">Ihostgcmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78aa5-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
