---
title: IHostGCManager::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 740f408b84dad67ee20c2508ae42a9569ed095f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179865"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="36f4f-102">IHostGCManager::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="36f4f-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="36f4f-103">Upozorňuje hostitele, který je vlákno, ze kterého bylo provedeno volání metody Chystáte se zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="36f4f-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f4f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36f4f-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="36f4f-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36f4f-105">Return Value</span></span>  
  
|<span data-ttu-id="36f4f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36f4f-106">HRESULT</span></span>|<span data-ttu-id="36f4f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="36f4f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36f4f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="36f4f-108">S_OK</span></span>|`ThreadIsBlockingForSuspension` <span data-ttu-id="36f4f-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="36f4f-109">returned successfully.</span></span>|  
|<span data-ttu-id="36f4f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36f4f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36f4f-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="36f4f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36f4f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36f4f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36f4f-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="36f4f-113">The call timed out.</span></span>|  
|<span data-ttu-id="36f4f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36f4f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36f4f-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="36f4f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36f4f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36f4f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36f4f-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="36f4f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36f4f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36f4f-118">E_FAIL</span></span>|<span data-ttu-id="36f4f-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="36f4f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36f4f-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="36f4f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36f4f-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36f4f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f4f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36f4f-122">Remarks</span></span>  
 <span data-ttu-id="36f4f-123">CLR volá obvykle `ThreadIsBlockForSuspension` metody v rámci přípravy pro uvolnění paměti, poskytnout možnost plánovanou zkoušku přeplánovat vlákno pro nespravované úloh hostitele.</span><span class="sxs-lookup"><span data-stu-id="36f4f-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36f4f-124">Hostitele mohou plánovanou zkoušku přeplánovat úlohy pouze po volání `ThreadIsBlockingForSuspension`.</span><span class="sxs-lookup"><span data-stu-id="36f4f-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="36f4f-125">Po modul runtime zavolá [suspensionstarting –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), hostitele nesmí plánovanou zkoušku přeplánovat úkolu.</span><span class="sxs-lookup"><span data-stu-id="36f4f-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36f4f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36f4f-126">Requirements</span></span>  
 <span data-ttu-id="36f4f-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f4f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f4f-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36f4f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36f4f-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36f4f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="36f4f-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="36f4f-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="36f4f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36f4f-131">See also</span></span>

- [<span data-ttu-id="36f4f-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36f4f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="36f4f-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36f4f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="36f4f-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36f4f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="36f4f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36f4f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="36f4f-136">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36f4f-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
