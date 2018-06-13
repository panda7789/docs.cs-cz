---
title: IHostGCManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eac8abede82915386abc19c4c8389932451df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440373"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="119d0-102">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119d0-102">IHostGCManager Interface</span></span>
<span data-ttu-id="119d0-103">Poskytuje metody, které hostitele události v kolekci mechanismus paměti implementované common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="119d0-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="119d0-104">Členové</span><span class="sxs-lookup"><span data-stu-id="119d0-104">Members</span></span>  
  
|<span data-ttu-id="119d0-105">Člen</span><span class="sxs-lookup"><span data-stu-id="119d0-105">Member</span></span>|<span data-ttu-id="119d0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="119d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="119d0-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="119d0-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="119d0-108">Upozorní hostitele, modul CLR obnovuje provádění úlohy na vláken, která měla bylo pozastaveno pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="119d0-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="119d0-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="119d0-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="119d0-110">Upozorní hostitele, modul CLR je pozastavení provádění úlohy, musíte provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="119d0-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="119d0-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="119d0-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="119d0-112">Upozorní na hostitele, vlákno, ze kterého bylo provedeno volání metody se rozhodli jste se blokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="119d0-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="119d0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="119d0-113">Requirements</span></span>  
 <span data-ttu-id="119d0-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119d0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119d0-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="119d0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="119d0-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="119d0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="119d0-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119d0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119d0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="119d0-118">See Also</span></span>  
 [<span data-ttu-id="119d0-119">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119d0-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="119d0-120">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119d0-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="119d0-121">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119d0-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="119d0-122">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119d0-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="119d0-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="119d0-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
