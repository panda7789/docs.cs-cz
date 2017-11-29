---
title: "IHostTaskManager::EndDelayAbort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.EndDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45148c506e2f6073dc175abe4397fad2172b355e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="c8175-102">IHostTaskManager::EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="c8175-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="c8175-103">Upozorní hostitele, který je spravovaný kód je ukončení období, ve kterém nesmí být aktuální úloha byla přerušena, následující starší volání [ihosttaskmanager::begindelayabort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8175-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8175-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8175-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c8175-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8175-105">Return Value</span></span>  
  
|<span data-ttu-id="c8175-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8175-106">HRESULT</span></span>|<span data-ttu-id="c8175-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c8175-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8175-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8175-108">S_OK</span></span>|<span data-ttu-id="c8175-109">`EndDelayAbort`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c8175-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="c8175-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8175-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8175-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c8175-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8175-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8175-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8175-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c8175-113">The call timed out.</span></span>|  
|<span data-ttu-id="c8175-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8175-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8175-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c8175-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8175-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8175-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8175-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c8175-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8175-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8175-118">E_FAIL</span></span>|<span data-ttu-id="c8175-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c8175-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8175-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c8175-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8175-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c8175-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c8175-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="c8175-122">E_UNEXPECTED</span></span>|<span data-ttu-id="c8175-123">`EndDelayAbort`byla volána bez odpovídající volání `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="c8175-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8175-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8175-124">Remarks</span></span>  
 <span data-ttu-id="c8175-125">Modul CLR zavolá odpovídající `BeginDelayAbort` na aktuální úlohy před voláním `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="c8175-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="c8175-126">Neexistuje odpovídající volání implementace hostitele [ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) by měla vrátit E_UNEXPECTED z `EndDelayAbort`a měli provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="c8175-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8175-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8175-127">Requirements</span></span>  
 <span data-ttu-id="c8175-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8175-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8175-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8175-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8175-130">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8175-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8175-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8175-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8175-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8175-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="c8175-133">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8175-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c8175-134">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8175-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c8175-135">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8175-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c8175-136">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8175-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
