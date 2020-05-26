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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804858"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="b05b0-102">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b05b0-102">IHostGCManager Interface</span></span>
<span data-ttu-id="b05b0-103">Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementovaného modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="b05b0-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="b05b0-104">Členové</span><span class="sxs-lookup"><span data-stu-id="b05b0-104">Members</span></span>  
  
|<span data-ttu-id="b05b0-105">Člen</span><span class="sxs-lookup"><span data-stu-id="b05b0-105">Member</span></span>|<span data-ttu-id="b05b0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b05b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b05b0-107">SuspensionEnding – metoda</span><span class="sxs-lookup"><span data-stu-id="b05b0-107">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="b05b0-108">Upozorňuje hostitele, že modul CLR pokračuje v provádění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b05b0-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="b05b0-109">SuspensionStarting – metoda</span><span class="sxs-lookup"><span data-stu-id="b05b0-109">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="b05b0-110">Upozorní hostitele, že modul CLR pozastaví provádění úloh a provede uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b05b0-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="b05b0-111">ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="b05b0-111">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="b05b0-112">Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b05b0-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b05b0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b05b0-113">Requirements</span></span>  
 <span data-ttu-id="b05b0-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b05b0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b05b0-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b05b0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b05b0-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b05b0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b05b0-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b05b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b05b0-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b05b0-118">See also</span></span>

- [<span data-ttu-id="b05b0-119">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b05b0-119">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b05b0-120">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b05b0-120">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b05b0-121">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b05b0-121">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b05b0-122">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b05b0-122">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b05b0-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b05b0-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
