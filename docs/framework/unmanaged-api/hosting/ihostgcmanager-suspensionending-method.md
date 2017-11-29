---
title: "IHostGCManager::SuspensionEnding – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9952e62d4979efa0d07b19f183ca71adcc643365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="3a85b-102">IHostGCManager::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="3a85b-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="3a85b-103">Upozorní hostitele, modul CLR (CLR) obnovuje provádění úlohy na vláken, která měla bylo pozastaveno pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3a85b-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a85b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a85b-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a85b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a85b-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="3a85b-106">[v] Generování kolekce paměti, který je právě nepřipojujte, ze kterého vlákno obnovuje.</span><span class="sxs-lookup"><span data-stu-id="3a85b-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a85b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3a85b-107">Return Value</span></span>  
  
|<span data-ttu-id="3a85b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a85b-108">HRESULT</span></span>|<span data-ttu-id="3a85b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3a85b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a85b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a85b-110">S_OK</span></span>|<span data-ttu-id="3a85b-111">`SuspensionEnding`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3a85b-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="3a85b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a85b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a85b-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3a85b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a85b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a85b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a85b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3a85b-115">The call timed out.</span></span>|  
|<span data-ttu-id="3a85b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a85b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a85b-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="3a85b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a85b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a85b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a85b-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="3a85b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a85b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a85b-120">E_FAIL</span></span>|<span data-ttu-id="3a85b-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="3a85b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a85b-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3a85b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a85b-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3a85b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a85b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a85b-124">Remarks</span></span>  
 <span data-ttu-id="3a85b-125">Volání CLR `SuspensionEnding` poté, co provede uvolňování hostitele informovat, že vlákno obnovuje provádění.</span><span class="sxs-lookup"><span data-stu-id="3a85b-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a85b-126">Vlákno, které bylo provedeno volání metody, které z nezměnila naplánování.</span><span class="sxs-lookup"><span data-stu-id="3a85b-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a85b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a85b-127">Requirements</span></span>  
 <span data-ttu-id="3a85b-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a85b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a85b-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a85b-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a85b-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a85b-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a85b-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a85b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a85b-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a85b-132">See Also</span></span>  
 [<span data-ttu-id="3a85b-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a85b-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3a85b-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a85b-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3a85b-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a85b-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3a85b-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a85b-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="3a85b-137">Ihostgcmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a85b-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
