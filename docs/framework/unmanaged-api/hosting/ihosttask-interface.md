---
title: "IHostTask – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask
helpviewer_keywords: IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a><span data-ttu-id="47ad0-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47ad0-102">IHostTask Interface</span></span>
<span data-ttu-id="47ad0-103">Poskytuje metody, které povolit modul CLR (CLR) ke komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="47ad0-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47ad0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="47ad0-104">Methods</span></span>  
  
|<span data-ttu-id="47ad0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-105">Method</span></span>|<span data-ttu-id="47ad0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="47ad0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47ad0-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="47ad0-108">Požadavky, že hostitel wake úlohu reprezentována aktuální `IHostTask` instance, takže úlohu můžete byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="47ad0-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="47ad0-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="47ad0-110">Získá přístup z více vláken úroveň priority úlohy reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="47ad0-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="47ad0-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="47ad0-112">Blokuje volání úkolů dokud je úloha reprezentována aktuální `IHostTask` instance dokončí, uplynutí zadaného časového intervalu nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="47ad0-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="47ad0-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="47ad0-114">Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="47ad0-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="47ad0-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="47ad0-116">Požadavky, že hostitel upravit prioritu podprocesu úrovně pro úlohu reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="47ad0-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="47ad0-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="47ad0-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="47ad0-118">Požadavky, že hostitel move – úloha reprezentována aktuální `IHostTask` instance z režimu spánku za provozu stavu, ve kterém můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="47ad0-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47ad0-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47ad0-119">Remarks</span></span>  
 <span data-ttu-id="47ad0-120">Modul CLR volá metody, které jsou definované `IHostTask` Pokud chcete spustit úlohu, nastavit její prioritu podprocesu úroveň, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="47ad0-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ad0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47ad0-121">Requirements</span></span>  
 <span data-ttu-id="47ad0-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ad0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ad0-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47ad0-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47ad0-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47ad0-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47ad0-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ad0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ad0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ad0-126">See Also</span></span>  
 [<span data-ttu-id="47ad0-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47ad0-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="47ad0-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47ad0-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="47ad0-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47ad0-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="47ad0-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="47ad0-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
