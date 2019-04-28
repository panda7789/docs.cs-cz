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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763578"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="116d9-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="116d9-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="116d9-103">Definuje metody, které umožňují hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.</span><span class="sxs-lookup"><span data-stu-id="116d9-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="116d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="116d9-104">Methods</span></span>  
  
|<span data-ttu-id="116d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="116d9-105">Method</span></span>|<span data-ttu-id="116d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="116d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="116d9-107">CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="116d9-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="116d9-108">Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="116d9-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="116d9-109">DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="116d9-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="116d9-110">Požadavky, že modul CLR zničit iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="116d9-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="116d9-111">GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="116d9-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="116d9-112">Získá úkol, který vlastní zadané monitorování.</span><span class="sxs-lookup"><span data-stu-id="116d9-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="116d9-113">GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="116d9-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="116d9-114">Získá další úkol, který čeká na uzamčení čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="116d9-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="116d9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="116d9-115">Requirements</span></span>  
 <span data-ttu-id="116d9-116">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="116d9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="116d9-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="116d9-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="116d9-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="116d9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="116d9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="116d9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116d9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="116d9-120">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="116d9-121">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="116d9-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="116d9-122">[Spravovaná a nespravovaná vlákna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="116d9-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="116d9-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="116d9-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
