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
ms.openlocfilehash: c40febb78c1bc78a5a724f559eb95869e90bdad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133078"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="178fe-102">IHostTaskManager::EndThreadAffinity – metoda</span><span class="sxs-lookup"><span data-stu-id="178fe-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="178fe-103">Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přesunuta do jiného vlákna operačního systému za předchozích volání [IHostTaskManager:: BeginThreadAffinity –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span><span class="sxs-lookup"><span data-stu-id="178fe-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="178fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="178fe-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="178fe-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="178fe-105">Return Value</span></span>  
  
|<span data-ttu-id="178fe-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="178fe-106">HRESULT</span></span>|<span data-ttu-id="178fe-107">Popis</span><span class="sxs-lookup"><span data-stu-id="178fe-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="178fe-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="178fe-108">S_OK</span></span>|<span data-ttu-id="178fe-109">`EndThreadAffinity` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="178fe-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="178fe-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="178fe-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="178fe-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="178fe-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="178fe-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="178fe-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="178fe-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="178fe-113">The call timed out.</span></span>|  
|<span data-ttu-id="178fe-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="178fe-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="178fe-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="178fe-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="178fe-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="178fe-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="178fe-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="178fe-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="178fe-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="178fe-118">E_FAIL</span></span>|<span data-ttu-id="178fe-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="178fe-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="178fe-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="178fe-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="178fe-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="178fe-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="178fe-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="178fe-122">E_UNEXPECTED</span></span>|<span data-ttu-id="178fe-123">`EndThreadAffinity` byla volána bez dřívějšího odpovídajícího volání `BeginThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="178fe-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="178fe-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="178fe-124">Remarks</span></span>  
 <span data-ttu-id="178fe-125">Modul CLR provede odpovídající volání `BeginThreadAffinity` u aktuální úlohy před voláním `EndThreadAffinity`.</span><span class="sxs-lookup"><span data-stu-id="178fe-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="178fe-126">V případě absence takového volání by implementace [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) hostitele měla vrátit E_UNEXPECTED a Neprovádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="178fe-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="178fe-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="178fe-127">Requirements</span></span>  
 <span data-ttu-id="178fe-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="178fe-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="178fe-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="178fe-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="178fe-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="178fe-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="178fe-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="178fe-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178fe-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="178fe-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="178fe-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="178fe-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="178fe-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="178fe-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="178fe-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="178fe-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="178fe-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="178fe-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
