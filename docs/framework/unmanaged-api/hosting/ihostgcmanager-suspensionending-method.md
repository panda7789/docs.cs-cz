---
title: IHostGCManager::SuspensionEnding – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 527607d5c39e7f698ab44baf4af0e7600ae2f473
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222819"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="e0b0e-102">IHostGCManager::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b0e-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="e0b0e-103">Upozorňuje hostitele, že modul CLR (CLR) obnovuje provádění úkolů na vlákna, která byla pozastavena pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0b0e-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0b0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0b0e-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="e0b0e-106">[in] Generaci uvolňování paměti, která je právě dokončení, ze které vlákno je obnovuje.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0b0e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e0b0e-107">Return Value</span></span>  
  
|<span data-ttu-id="e0b0e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0b0e-108">HRESULT</span></span>|<span data-ttu-id="e0b0e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e0b0e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0b0e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0b0e-110">S_OK</span></span>|`SuspensionEnding` <span data-ttu-id="e0b0e-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-111">returned successfully.</span></span>|  
|<span data-ttu-id="e0b0e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0b0e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0b0e-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0b0e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0b0e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0b0e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-115">The call timed out.</span></span>|  
|<span data-ttu-id="e0b0e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0b0e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0b0e-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0b0e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0b0e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0b0e-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0b0e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0b0e-120">E_FAIL</span></span>|<span data-ttu-id="e0b0e-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0b0e-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0b0e-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0b0e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0b0e-124">Remarks</span></span>  
 <span data-ttu-id="e0b0e-125">Volání CLR `SuspensionEnding` poté, co provede uvolnění, informovat hostitele, že vlákno obnovuje spuštění.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e0b0e-126">Není plánovanou zkoušku přeplánovat, které bylo provedeno volání metody z vlákna.</span><span class="sxs-lookup"><span data-stu-id="e0b0e-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b0e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0b0e-127">Requirements</span></span>  
 <span data-ttu-id="e0b0e-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0b0e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b0e-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0b0e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0b0e-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0b0e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e0b0e-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e0b0e-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e0b0e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0b0e-132">See also</span></span>

- [<span data-ttu-id="e0b0e-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b0e-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e0b0e-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b0e-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e0b0e-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b0e-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e0b0e-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b0e-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="e0b0e-137">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0b0e-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
