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
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081499"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="f6466-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6466-102">IHostTask Interface</span></span>
<span data-ttu-id="f6466-103">Poskytuje metody, které umožňují common language runtime (CLR) ke komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="f6466-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6466-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f6466-104">Methods</span></span>  
  
|<span data-ttu-id="f6466-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-105">Method</span></span>|<span data-ttu-id="f6466-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f6466-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6466-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="f6466-108">Požadavky, že hostitel probuzení úloh reprezentovaný aktuální `IHostTask` instance, tak můžete přeruší úlohu.</span><span class="sxs-lookup"><span data-stu-id="f6466-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="f6466-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="f6466-110">Získá úroveň priority vlákna úloh reprezentovaný aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="f6466-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="f6466-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="f6466-112">Blokuje volající úlohou, dokud není úloha reprezentované aktuální `IHostTask` instance dokončení, o zadaný časový interval uplyne, nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="f6466-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="f6466-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="f6466-114">Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="f6466-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="f6466-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="f6466-116">Požadavky, že hostitel upravit priorita vlákna na úrovni úkolů reprezentované aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="f6466-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="f6466-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="f6466-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="f6466-118">Požadavky, že hostitel move – úloha reprezentované aktuální `IHostTask` instanci z režimu spánku za provozu stavu, ve kterém lze kód spustit.</span><span class="sxs-lookup"><span data-stu-id="f6466-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6466-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6466-119">Remarks</span></span>  
 <span data-ttu-id="f6466-120">CLR volá metody definované `IHostTask` spuštění úlohy, nastavit její prioritu vlákna úroveň, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f6466-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6466-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6466-121">Requirements</span></span>  
 <span data-ttu-id="f6466-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6466-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6466-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f6466-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6466-124">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6466-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6466-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6466-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6466-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6466-126">See also</span></span>

- [<span data-ttu-id="f6466-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6466-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f6466-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6466-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f6466-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6466-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f6466-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f6466-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
