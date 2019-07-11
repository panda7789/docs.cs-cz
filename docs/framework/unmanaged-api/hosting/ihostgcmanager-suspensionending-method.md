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
ms.openlocfilehash: 9a815d1a5e8b40aee84ca2b9971ae4be7fb2c725
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763727"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="51621-102">IHostGCManager::SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="51621-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="51621-103">Upozorňuje hostitele, že modul CLR (CLR) obnovuje provádění úkolů na vlákna, která byla pozastavena pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="51621-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51621-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51621-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51621-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51621-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="51621-106">[in] Generaci uvolňování paměti, která je právě dokončení, ze které vlákno je obnovuje.</span><span class="sxs-lookup"><span data-stu-id="51621-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51621-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="51621-107">Return Value</span></span>  
  
|<span data-ttu-id="51621-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51621-108">HRESULT</span></span>|<span data-ttu-id="51621-109">Popis</span><span class="sxs-lookup"><span data-stu-id="51621-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51621-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51621-110">S_OK</span></span>|<span data-ttu-id="51621-111">`SuspensionEnding` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="51621-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="51621-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51621-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51621-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="51621-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51621-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51621-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51621-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="51621-115">The call timed out.</span></span>|  
|<span data-ttu-id="51621-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51621-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51621-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="51621-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51621-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51621-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51621-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="51621-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51621-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51621-120">E_FAIL</span></span>|<span data-ttu-id="51621-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="51621-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51621-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="51621-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51621-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="51621-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51621-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51621-124">Remarks</span></span>  
 <span data-ttu-id="51621-125">Volání CLR `SuspensionEnding` poté, co provede uvolnění, informovat hostitele, že vlákno obnovuje spuštění.</span><span class="sxs-lookup"><span data-stu-id="51621-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="51621-126">Není plánovanou zkoušku přeplánovat, které bylo provedeno volání metody z vlákna.</span><span class="sxs-lookup"><span data-stu-id="51621-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51621-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51621-127">Requirements</span></span>  
 <span data-ttu-id="51621-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51621-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51621-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51621-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51621-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51621-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51621-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51621-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51621-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51621-132">See also</span></span>

- [<span data-ttu-id="51621-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51621-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="51621-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51621-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="51621-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51621-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="51621-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51621-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="51621-137">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51621-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
