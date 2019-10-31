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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121397"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="2f4b2-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f4b2-102">IHostTask Interface</span></span>
<span data-ttu-id="2f4b2-103">Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) komunikoval s hostitelem a spravoval úlohy.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f4b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f4b2-104">Methods</span></span>  
  
|<span data-ttu-id="2f4b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-105">Method</span></span>|<span data-ttu-id="2f4b2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2f4b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f4b2-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="2f4b2-108">Vyžádá, aby hostitel probudil úlohu reprezentovanou aktuální instancí `IHostTask`, takže úkol může být přerušen.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="2f4b2-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="2f4b2-110">Získá úroveň priority vlákna úlohy reprezentované aktuální instancí `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="2f4b2-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="2f4b2-112">Zablokuje volající úlohu, dokud se nedokončí úkol, který je reprezentován aktuální `IHostTask` instance, zadaného časového intervalu vypršela nebo [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="2f4b2-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="2f4b2-114">Přidruží instanci [rozhraní ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) k aktuální instanci `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="2f4b2-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="2f4b2-116">Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální instancí `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="2f4b2-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="2f4b2-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="2f4b2-118">Požaduje, aby hostitel přesunul úlohu představovanou aktuální `IHostTask` instance z pozastaveného stavu do aktivního stavu, ve kterém lze kód spustit.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f4b2-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f4b2-119">Remarks</span></span>  
 <span data-ttu-id="2f4b2-120">CLR volá metody definované `IHostTask` pro spuštění úlohy, nastavení úrovně priority vlákna a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2f4b2-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f4b2-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f4b2-121">Requirements</span></span>  
 <span data-ttu-id="2f4b2-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f4b2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f4b2-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f4b2-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f4b2-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f4b2-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f4b2-125">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f4b2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f4b2-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f4b2-126">See also</span></span>

- [<span data-ttu-id="2f4b2-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f4b2-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="2f4b2-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f4b2-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f4b2-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f4b2-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="2f4b2-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2f4b2-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
