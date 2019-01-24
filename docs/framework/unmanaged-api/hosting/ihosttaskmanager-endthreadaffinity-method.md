---
title: IHostTaskManager::EndThreadAffinity – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8de8816f08fa98055bb397d77d060721a0fb30d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557913"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="50d3d-102">IHostTaskManager::EndThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="50d3d-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="50d3d-103">Upozorní na hostitele, spravovaný kód se ukončuje období, ve kterém nesmí být aktuálního úkolu přesunuty do jinému vláknu operačního systému po dřívějším volání [ihosttaskmanager::beginthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="50d3d-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50d3d-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50d3d-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50d3d-105">Return Value</span></span>  
  
|<span data-ttu-id="50d3d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50d3d-106">HRESULT</span></span>|<span data-ttu-id="50d3d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="50d3d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50d3d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="50d3d-108">S_OK</span></span>|<span data-ttu-id="50d3d-109">`EndThreadAffinity` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="50d3d-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="50d3d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50d3d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50d3d-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="50d3d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50d3d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50d3d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50d3d-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="50d3d-113">The call timed out.</span></span>|  
|<span data-ttu-id="50d3d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50d3d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50d3d-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="50d3d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50d3d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50d3d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50d3d-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="50d3d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50d3d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50d3d-118">E_FAIL</span></span>|<span data-ttu-id="50d3d-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="50d3d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50d3d-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="50d3d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50d3d-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50d3d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50d3d-122">E_UNEXPECTED, JE-</span><span class="sxs-lookup"><span data-stu-id="50d3d-122">E_UNEXPECTED</span></span>|<span data-ttu-id="50d3d-123">`EndThreadAffinity` byla volána bez dříve odpovídající volání `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="50d3d-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50d3d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50d3d-124">Remarks</span></span>  
 <span data-ttu-id="50d3d-125">Modul CLR provede odpovídající volání `BeginThreadAffinity` v aktuální úloze před voláním `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="50d3d-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="50d3d-126">Chybí odpovídající volání provádění hostitele [ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) by měl vrátí e_unexpected, je- a Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="50d3d-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50d3d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50d3d-127">Requirements</span></span>  
 <span data-ttu-id="50d3d-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50d3d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50d3d-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50d3d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50d3d-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50d3d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50d3d-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50d3d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d3d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50d3d-132">See also</span></span>
- <xref:System.Threading>
- [<span data-ttu-id="50d3d-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50d3d-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="50d3d-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50d3d-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="50d3d-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50d3d-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="50d3d-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50d3d-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
