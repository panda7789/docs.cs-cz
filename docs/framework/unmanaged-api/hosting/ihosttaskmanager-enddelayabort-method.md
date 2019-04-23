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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194443"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="e5ca5-102">IHostTaskManager::EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="e5ca5-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="e5ca5-103">Upozorní na hostitele, spravovaný kód se ukončuje období, ve kterém nesmí být aktuální úloha přerušena, po dřívějším volání [ihosttaskmanager::begindelayabort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5ca5-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ca5-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e5ca5-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e5ca5-105">Return Value</span></span>  
  
|<span data-ttu-id="e5ca5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5ca5-106">HRESULT</span></span>|<span data-ttu-id="e5ca5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e5ca5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5ca5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5ca5-108">S_OK</span></span>|<span data-ttu-id="e5ca5-109">`EndDelayAbort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="e5ca5-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e5ca5-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e5ca5-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e5ca5-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e5ca5-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e5ca5-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-113">The call timed out.</span></span>|  
|<span data-ttu-id="e5ca5-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e5ca5-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e5ca5-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e5ca5-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e5ca5-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e5ca5-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e5ca5-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e5ca5-118">E_FAIL</span></span>|<span data-ttu-id="e5ca5-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e5ca5-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e5ca5-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e5ca5-122">E_UNEXPECTED, JE-</span><span class="sxs-lookup"><span data-stu-id="e5ca5-122">E_UNEXPECTED</span></span>|<span data-ttu-id="e5ca5-123">`EndDelayAbort` byla volána bez odpovídajícího volání `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5ca5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5ca5-124">Remarks</span></span>  
 <span data-ttu-id="e5ca5-125">Modul CLR provede odpovídající volání `BeginDelayAbort` v aktuální úloze před voláním `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="e5ca5-126">Chybí odpovídající volání provádění hostitele [ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) by měla vrátit e_unexpected, je-z `EndDelayAbort`a neměla by mít žádné akce.</span><span class="sxs-lookup"><span data-stu-id="e5ca5-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ca5-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5ca5-127">Requirements</span></span>  
 <span data-ttu-id="e5ca5-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ca5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ca5-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5ca5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5ca5-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5ca5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5ca5-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ca5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ca5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5ca5-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="e5ca5-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5ca5-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e5ca5-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5ca5-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e5ca5-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5ca5-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e5ca5-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5ca5-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
