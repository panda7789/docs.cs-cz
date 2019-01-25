---
title: IHostTask – rozhraní
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d862c02e96487049fb88f80665d32caf6939ed1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555935"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="851d9-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851d9-102">IHostTask Interface</span></span>
<span data-ttu-id="851d9-103">Poskytuje metody, které umožňují common language runtime (CLR) ke komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="851d9-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="851d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="851d9-104">Methods</span></span>  
  
|<span data-ttu-id="851d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-105">Method</span></span>|<span data-ttu-id="851d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="851d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="851d9-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="851d9-108">Požadavky, že hostitel probuzení úloh reprezentovaný aktuální `IHostTask` instance, tak můžete přeruší úlohu.</span><span class="sxs-lookup"><span data-stu-id="851d9-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="851d9-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="851d9-110">Získá úroveň priority vlákna úloh reprezentovaný aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="851d9-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="851d9-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="851d9-112">Blokuje volající úlohou, dokud není úloha reprezentované aktuální `IHostTask` instance dokončení, o zadaný časový interval uplyne, nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="851d9-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="851d9-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="851d9-114">Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="851d9-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="851d9-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="851d9-116">Požadavky, že hostitel upravit priorita vlákna na úrovni úkolů reprezentované aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="851d9-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="851d9-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="851d9-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="851d9-118">Požadavky, že hostitel move – úloha reprezentované aktuální `IHostTask` instanci z režimu spánku za provozu stavu, ve kterém lze kód spustit.</span><span class="sxs-lookup"><span data-stu-id="851d9-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="851d9-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="851d9-119">Remarks</span></span>  
 <span data-ttu-id="851d9-120">CLR volá metody definované `IHostTask` spuštění úlohy, nastavit její prioritu vlákna úroveň, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="851d9-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="851d9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="851d9-121">Requirements</span></span>  
 <span data-ttu-id="851d9-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="851d9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="851d9-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="851d9-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="851d9-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="851d9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="851d9-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="851d9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="851d9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="851d9-126">See also</span></span>
- [<span data-ttu-id="851d9-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851d9-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="851d9-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851d9-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="851d9-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="851d9-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="851d9-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="851d9-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
