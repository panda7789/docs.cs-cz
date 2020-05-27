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
ms.openlocfilehash: f8f476f681764a46700dd5ec83c8f9b2739f18f6
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842488"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="8b62f-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b62f-102">IHostTask Interface</span></span>
<span data-ttu-id="8b62f-103">Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) komunikoval s hostitelem a spravoval úlohy.</span><span class="sxs-lookup"><span data-stu-id="8b62f-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b62f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b62f-104">Methods</span></span>  
  
|<span data-ttu-id="8b62f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-105">Method</span></span>|<span data-ttu-id="8b62f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8b62f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b62f-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-107">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="8b62f-108">Požaduje, aby hostitel probudil úlohu reprezentovanou aktuální `IHostTask` instancí, aby bylo možné úlohu přerušit.</span><span class="sxs-lookup"><span data-stu-id="8b62f-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="8b62f-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-109">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="8b62f-110">Získá úroveň priority vlákna úkolu reprezentované aktuální `IHostTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="8b62f-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="8b62f-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="8b62f-112">Zablokuje volající úlohu, dokud není dokončena úloha reprezentovaná aktuální `IHostTask` instancí, zadaný časový interval vypršel nebo je volána metoda [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8b62f-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="8b62f-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="8b62f-114">Přidruží instanci [rozhraní ICLRTask](iclrtask-interface.md) k aktuální `IHostTask` instanci.</span><span class="sxs-lookup"><span data-stu-id="8b62f-114">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="8b62f-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-115">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="8b62f-116">Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální `IHostTask` instancí.</span><span class="sxs-lookup"><span data-stu-id="8b62f-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="8b62f-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="8b62f-117">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="8b62f-118">Požaduje, aby hostitel přesunul úlohu představovanou aktuální `IHostTask` instancí z pozastaveného stavu do aktivního stavu, ve kterém lze spustit kód.</span><span class="sxs-lookup"><span data-stu-id="8b62f-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b62f-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b62f-119">Remarks</span></span>  
 <span data-ttu-id="8b62f-120">CLR volá metody definované `IHostTask` pro spuštění úlohy, nastavení úrovně priority vlákna a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8b62f-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b62f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b62f-121">Requirements</span></span>  
 <span data-ttu-id="8b62f-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b62f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b62f-123">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b62f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b62f-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b62f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b62f-125">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b62f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b62f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b62f-126">See also</span></span>

- [<span data-ttu-id="8b62f-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b62f-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8b62f-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b62f-128">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8b62f-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b62f-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8b62f-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8b62f-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
