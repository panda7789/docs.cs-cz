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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203090"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="2d30d-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d30d-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="2d30d-103">Definuje metody, které umožňují hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.</span><span class="sxs-lookup"><span data-stu-id="2d30d-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d30d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d30d-104">Methods</span></span>  
  
|<span data-ttu-id="2d30d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d30d-105">Method</span></span>|<span data-ttu-id="2d30d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2d30d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d30d-107">CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="2d30d-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="2d30d-108">Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="2d30d-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="2d30d-109">DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="2d30d-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="2d30d-110">Požadavky, že modul CLR zničit iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="2d30d-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="2d30d-111">GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="2d30d-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="2d30d-112">Získá úkol, který vlastní zadané monitorování.</span><span class="sxs-lookup"><span data-stu-id="2d30d-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="2d30d-113">GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="2d30d-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="2d30d-114">Získá další úkol, který čeká na uzamčení čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="2d30d-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d30d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d30d-115">Requirements</span></span>  
 <span data-ttu-id="2d30d-116">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d30d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d30d-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d30d-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d30d-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d30d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2d30d-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2d30d-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d30d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d30d-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="2d30d-121">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d30d-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="2d30d-122">Spravovaná a nespravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2d30d-122">Managed and Unmanaged Threading</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [<span data-ttu-id="2d30d-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="2d30d-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
