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
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130483"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="71ef6-102">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71ef6-102">IHostGCManager Interface</span></span>
<span data-ttu-id="71ef6-103">Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementovaného modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="71ef6-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="71ef6-104">Členové</span><span class="sxs-lookup"><span data-stu-id="71ef6-104">Members</span></span>  
  
|<span data-ttu-id="71ef6-105">Člen</span><span class="sxs-lookup"><span data-stu-id="71ef6-105">Member</span></span>|<span data-ttu-id="71ef6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="71ef6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71ef6-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="71ef6-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="71ef6-108">Upozorňuje hostitele, že modul CLR pokračuje v provádění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="71ef6-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="71ef6-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="71ef6-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="71ef6-110">Upozorní hostitele, že modul CLR pozastaví provádění úloh a provede uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="71ef6-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="71ef6-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="71ef6-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="71ef6-112">Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="71ef6-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71ef6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71ef6-113">Requirements</span></span>  
 <span data-ttu-id="71ef6-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71ef6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ef6-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71ef6-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71ef6-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="71ef6-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71ef6-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ef6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ef6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71ef6-118">See also</span></span>

- [<span data-ttu-id="71ef6-119">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71ef6-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="71ef6-120">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71ef6-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="71ef6-121">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71ef6-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="71ef6-122">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71ef6-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="71ef6-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="71ef6-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
