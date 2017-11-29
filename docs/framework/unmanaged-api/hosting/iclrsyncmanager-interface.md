---
title: "ICLRSyncManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="49811-102">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49811-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="49811-103">Definuje metody, které umožňují hostitele k načtení informací o požadovaných úkolů a ke zjištění zablokování v jeho implementaci synchronizace.</span><span class="sxs-lookup"><span data-stu-id="49811-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49811-104">Metody</span><span class="sxs-lookup"><span data-stu-id="49811-104">Methods</span></span>  
  
|<span data-ttu-id="49811-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="49811-105">Method</span></span>|<span data-ttu-id="49811-106">Popis</span><span class="sxs-lookup"><span data-stu-id="49811-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49811-107">Createrwlockowneriterator – metoda</span><span class="sxs-lookup"><span data-stu-id="49811-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="49811-108">Požadavky, které modul CLR (CLR) vytvořit iterace pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="49811-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="49811-109">Deleterwlockowneriterator – metoda</span><span class="sxs-lookup"><span data-stu-id="49811-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="49811-110">Požadavky, že modulu CLR destroy iterátor, který byl vytvořen volání `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="49811-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="49811-111">Getmonitorowner – metoda</span><span class="sxs-lookup"><span data-stu-id="49811-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="49811-112">Získá úloha, která vlastní zadaný monitorování.</span><span class="sxs-lookup"><span data-stu-id="49811-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="49811-113">Getrwlockownernext – metoda</span><span class="sxs-lookup"><span data-stu-id="49811-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="49811-114">Získá další úloha, která čeká na aktuální zámek čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="49811-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49811-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49811-115">Requirements</span></span>  
 <span data-ttu-id="49811-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49811-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49811-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="49811-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49811-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49811-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49811-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49811-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49811-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="49811-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="49811-121">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49811-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="49811-122">Spravovaná a nespravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="49811-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="49811-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="49811-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
