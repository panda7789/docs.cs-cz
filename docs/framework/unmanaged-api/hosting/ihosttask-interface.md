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
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442218"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="9983c-102">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9983c-102">IHostTask Interface</span></span>
<span data-ttu-id="9983c-103">Poskytuje metody, které povolit modul CLR (CLR) ke komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="9983c-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9983c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9983c-104">Methods</span></span>  
  
|<span data-ttu-id="9983c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-105">Method</span></span>|<span data-ttu-id="9983c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9983c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9983c-107">Alert – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="9983c-108">Požadavky, že hostitel wake úlohu reprezentována aktuální `IHostTask` instance, takže úlohu můžete byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="9983c-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="9983c-109">GetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="9983c-110">Získá přístup z více vláken úroveň priority úlohy reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="9983c-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="9983c-111">Join – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="9983c-112">Blokuje volání úkolů dokud je úloha reprezentována aktuální `IHostTask` instance dokončí, uplynutí zadaného časového intervalu nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.</span><span class="sxs-lookup"><span data-stu-id="9983c-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="9983c-113">SetCLRTask – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="9983c-114">Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="9983c-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="9983c-115">SetPriority – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="9983c-116">Požadavky, že hostitel upravit prioritu podprocesu úrovně pro úlohu reprezentována aktuální `IHostTask` instance.</span><span class="sxs-lookup"><span data-stu-id="9983c-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="9983c-117">Start – metoda</span><span class="sxs-lookup"><span data-stu-id="9983c-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="9983c-118">Požadavky, že hostitel move – úloha reprezentována aktuální `IHostTask` instance z režimu spánku za provozu stavu, ve kterém můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="9983c-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9983c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9983c-119">Remarks</span></span>  
 <span data-ttu-id="9983c-120">Modul CLR volá metody, které jsou definované `IHostTask` Pokud chcete spustit úlohu, nastavit její prioritu podprocesu úroveň, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9983c-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9983c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9983c-121">Requirements</span></span>  
 <span data-ttu-id="9983c-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9983c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9983c-123">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9983c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9983c-124">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9983c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9983c-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9983c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9983c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="9983c-126">See Also</span></span>  
 [<span data-ttu-id="9983c-127">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9983c-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9983c-128">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9983c-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9983c-129">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9983c-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="9983c-130">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9983c-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
