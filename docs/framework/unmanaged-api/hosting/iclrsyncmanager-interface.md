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
ms.openlocfilehash: ede896cdb93217fcfba9d66ed7102bcc1ba762e9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129321"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="79876-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79876-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="79876-103">Definuje metody, které umožňují hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.</span><span class="sxs-lookup"><span data-stu-id="79876-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79876-104">Metody</span><span class="sxs-lookup"><span data-stu-id="79876-104">Methods</span></span>  
  
|<span data-ttu-id="79876-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="79876-105">Method</span></span>|<span data-ttu-id="79876-106">Popis</span><span class="sxs-lookup"><span data-stu-id="79876-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79876-107">CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="79876-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="79876-108">Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="79876-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="79876-109">DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="79876-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="79876-110">Požadavky, že modul CLR zničit iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="79876-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="79876-111">GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="79876-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="79876-112">Získá úkol, který vlastní zadané monitorování.</span><span class="sxs-lookup"><span data-stu-id="79876-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="79876-113">GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="79876-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="79876-114">Získá další úkol, který čeká na uzamčení čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="79876-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79876-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79876-115">Requirements</span></span>  
 <span data-ttu-id="79876-116">**Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79876-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79876-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79876-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79876-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79876-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79876-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79876-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79876-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="79876-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="79876-121">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79876-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="79876-122">[Spravovaná a nespravovaná vlákna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79876-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>  
 [<span data-ttu-id="79876-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="79876-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
