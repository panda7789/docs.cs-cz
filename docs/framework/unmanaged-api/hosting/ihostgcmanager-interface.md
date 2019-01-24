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
ms.openlocfilehash: eaf5a0061b068d9adea3f6aeb28f9b6bb20c3174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710249"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="d6205-102">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6205-102">IHostGCManager Interface</span></span>
<span data-ttu-id="d6205-103">Poskytuje metody, které upozornil hostitele události v mechanismu kolekce uvolnění paměti implementován modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d6205-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="d6205-104">Členové</span><span class="sxs-lookup"><span data-stu-id="d6205-104">Members</span></span>  
  
|<span data-ttu-id="d6205-105">Člen</span><span class="sxs-lookup"><span data-stu-id="d6205-105">Member</span></span>|<span data-ttu-id="d6205-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d6205-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6205-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="d6205-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="d6205-108">Upozorňuje hostitele, že modul CLR obnovuje provádění úkolů na vlákna, která byla pozastavena pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6205-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="d6205-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="d6205-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="d6205-110">Upozorňuje hostitele, že modul CLR je pozastavení provádění úkolů, k provedení uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6205-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="d6205-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="d6205-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="d6205-112">Upozorňuje hostitele, který je vlákno, ze kterého bylo provedeno volání metody Chystáte se zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d6205-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6205-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6205-113">Requirements</span></span>  
 <span data-ttu-id="d6205-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6205-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6205-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6205-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6205-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6205-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6205-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6205-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6205-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6205-118">See also</span></span>
- [<span data-ttu-id="d6205-119">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6205-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d6205-120">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6205-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d6205-121">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6205-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d6205-122">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6205-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="d6205-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d6205-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
