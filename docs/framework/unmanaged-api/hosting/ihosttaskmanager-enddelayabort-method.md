---
title: IHostTaskManager::EndDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: cf79c0d0f6def46d7f4d55f17afbd1f1dff00ad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133074"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="23a42-102">IHostTaskManager::EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="23a42-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="23a42-103">Upozorní hostitele, že spravovaný kód ukončuje období, ve kterém nesmí být aktuální úloha přerušena, po předchozím volání metody [IHostTaskManager:: BeginDelayAbort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="23a42-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23a42-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="23a42-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="23a42-105">Return Value</span></span>  
  
|<span data-ttu-id="23a42-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23a42-106">HRESULT</span></span>|<span data-ttu-id="23a42-107">Popis</span><span class="sxs-lookup"><span data-stu-id="23a42-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23a42-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="23a42-108">S_OK</span></span>|<span data-ttu-id="23a42-109">`EndDelayAbort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="23a42-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="23a42-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23a42-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23a42-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="23a42-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="23a42-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="23a42-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="23a42-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="23a42-113">The call timed out.</span></span>|  
|<span data-ttu-id="23a42-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="23a42-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="23a42-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="23a42-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="23a42-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="23a42-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="23a42-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="23a42-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="23a42-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23a42-118">E_FAIL</span></span>|<span data-ttu-id="23a42-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="23a42-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="23a42-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="23a42-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="23a42-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="23a42-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="23a42-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="23a42-122">E_UNEXPECTED</span></span>|<span data-ttu-id="23a42-123">`EndDelayAbort` byla volána bez odpovídajícího volání `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="23a42-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23a42-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23a42-124">Remarks</span></span>  
 <span data-ttu-id="23a42-125">Modul CLR provede odpovídající volání `BeginDelayAbort` u aktuální úlohy před voláním `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="23a42-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="23a42-126">V případě absence takového volání by implementace [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) hostitele měla vrátit E_UNEXPECTED z `EndDelayAbort`a neměla by mít žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="23a42-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a42-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23a42-127">Requirements</span></span>  
 <span data-ttu-id="23a42-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a42-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a42-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="23a42-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23a42-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="23a42-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23a42-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a42-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a42-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23a42-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="23a42-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a42-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="23a42-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a42-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="23a42-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a42-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="23a42-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23a42-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
