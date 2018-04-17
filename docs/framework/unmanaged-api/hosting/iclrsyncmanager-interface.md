---
title: ICLRSyncManager – rozhraní
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17a1e3073713b54cb7a68e6ba3ef2562d4fbcaeb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="93bdb-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93bdb-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="93bdb-103">Definuje metody, které umožňují hostitele k načtení informací o požadovaných úkolů a ke zjištění zablokování v jeho implementaci synchronizace.</span><span class="sxs-lookup"><span data-stu-id="93bdb-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93bdb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93bdb-104">Methods</span></span>  
  
|<span data-ttu-id="93bdb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93bdb-105">Method</span></span>|<span data-ttu-id="93bdb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="93bdb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93bdb-107">CreateRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="93bdb-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="93bdb-108">Požadavky, které modul CLR (CLR) vytvořit iterace pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="93bdb-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="93bdb-109">DeleteRWLockOwnerIterator – metoda</span><span class="sxs-lookup"><span data-stu-id="93bdb-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="93bdb-110">Požadavky, že modulu CLR destroy iterátor, který byl vytvořen volání `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="93bdb-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="93bdb-111">GetMonitorOwner – metoda</span><span class="sxs-lookup"><span data-stu-id="93bdb-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="93bdb-112">Získá úloha, která vlastní zadaný monitorování.</span><span class="sxs-lookup"><span data-stu-id="93bdb-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="93bdb-113">GetRWLockOwnerNext – metoda</span><span class="sxs-lookup"><span data-stu-id="93bdb-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="93bdb-114">Získá další úloha, která čeká na aktuální zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="93bdb-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93bdb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93bdb-115">Requirements</span></span>  
 <span data-ttu-id="93bdb-116">**Platformy:** najdete v části [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93bdb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bdb-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93bdb-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93bdb-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93bdb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93bdb-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bdb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bdb-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="93bdb-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="93bdb-121">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93bdb-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="93bdb-122">[Spravovaná a nespravovaná vlákna](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="93bdb-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="93bdb-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="93bdb-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
