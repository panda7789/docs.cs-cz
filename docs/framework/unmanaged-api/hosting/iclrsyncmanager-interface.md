---
title: ICLRSyncManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133923"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="f218b-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f218b-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="f218b-103">Definuje metody, které umožní hostiteli získat informace o požadovaných úlohách a zjišťovat zablokování v jeho implementaci synchronizace.</span><span class="sxs-lookup"><span data-stu-id="f218b-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f218b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f218b-104">Methods</span></span>  
  
|<span data-ttu-id="f218b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f218b-105">Method</span></span>|<span data-ttu-id="f218b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f218b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f218b-107">CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="f218b-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="f218b-108">Požadavky, které modul CLR (Common Language Runtime) vytvoří iterátor, který může hostitel použít k určení sady úloh čekajících na zámek pro zápis čtenářů.</span><span class="sxs-lookup"><span data-stu-id="f218b-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="f218b-109">DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="f218b-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="f218b-110">Požaduje, aby modul CLR zničil iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="f218b-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="f218b-111">GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="f218b-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="f218b-112">Získá úkol, který vlastní zadané monitorování.</span><span class="sxs-lookup"><span data-stu-id="f218b-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="f218b-113">GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="f218b-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="f218b-114">Získá další úkol, který čeká na aktuální zámek zapisovače pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f218b-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f218b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f218b-115">Requirements</span></span>  
 <span data-ttu-id="f218b-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f218b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f218b-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f218b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f218b-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f218b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f218b-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f218b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f218b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f218b-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="f218b-121">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f218b-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="f218b-122">[Spravované a nespravované zřetězení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f218b-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="f218b-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f218b-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
