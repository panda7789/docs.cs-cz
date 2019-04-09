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
ms.openlocfilehash: 3f94f365aa8c9221c64e9611deab3597e06ed862
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157895"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="2e9ee-102">IHostTaskManager::EndThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="2e9ee-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="2e9ee-103">Upozorní na hostitele, spravovaný kód se ukončuje období, ve kterém nesmí být aktuálního úkolu přesunuty do jinému vláknu operačního systému po dřívějším volání [ihosttaskmanager::beginthreadaffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="2e9ee-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e9ee-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2e9ee-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e9ee-105">Return Value</span></span>  
  
|<span data-ttu-id="2e9ee-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e9ee-106">HRESULT</span></span>|<span data-ttu-id="2e9ee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e9ee-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e9ee-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e9ee-108">S_OK</span></span>|`EndThreadAffinity` <span data-ttu-id="2e9ee-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-109">returned successfully.</span></span>|  
|<span data-ttu-id="2e9ee-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e9ee-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e9ee-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e9ee-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e9ee-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e9ee-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-113">The call timed out.</span></span>|  
|<span data-ttu-id="2e9ee-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e9ee-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e9ee-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e9ee-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e9ee-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e9ee-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e9ee-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e9ee-118">E_FAIL</span></span>|<span data-ttu-id="2e9ee-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e9ee-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e9ee-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2e9ee-122">E_UNEXPECTED, JE-</span><span class="sxs-lookup"><span data-stu-id="2e9ee-122">E_UNEXPECTED</span></span>|`EndThreadAffinity` <span data-ttu-id="2e9ee-123">byla volána bez dříve odpovídající volání `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-123">was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e9ee-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e9ee-124">Remarks</span></span>  
 <span data-ttu-id="2e9ee-125">Modul CLR provede odpovídající volání `BeginThreadAffinity` v aktuální úloze před voláním `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="2e9ee-126">Chybí odpovídající volání provádění hostitele [ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) by měl vrátí e_unexpected, je- a Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="2e9ee-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9ee-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e9ee-127">Requirements</span></span>  
 <span data-ttu-id="2e9ee-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e9ee-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9ee-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2e9ee-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e9ee-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e9ee-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2e9ee-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e9ee-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e9ee-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e9ee-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="2e9ee-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e9ee-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2e9ee-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e9ee-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2e9ee-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e9ee-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="2e9ee-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e9ee-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
