---
title: "ETaskType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ETaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ETaskType
helpviewer_keywords: ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7973b8cbd49858daaf6f08d55c7d9f60f687a72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="229ca-102">ETaskType – výčet</span><span class="sxs-lookup"><span data-stu-id="229ca-102">ETaskType Enumeration</span></span>
<span data-ttu-id="229ca-103">Obsahuje hodnoty, které označují typ úlohy, která je reprezentována buď [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) nebo [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="229ca-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="229ca-104">Syntax</span></span>  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="229ca-105">Členové</span><span class="sxs-lookup"><span data-stu-id="229ca-105">Members</span></span>  
  
|<span data-ttu-id="229ca-106">Člen</span><span class="sxs-lookup"><span data-stu-id="229ca-106">Member</span></span>|<span data-ttu-id="229ca-107">Popis</span><span class="sxs-lookup"><span data-stu-id="229ca-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="229ca-108">Rozhraní představuje úkol uvolnění domény aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="229ca-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="229ca-109">Rozhraní představuje úlohu pomocná ladicí program.</span><span class="sxs-lookup"><span data-stu-id="229ca-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="229ca-110">Rozhraní představuje úlohu finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="229ca-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="229ca-111">Rozhraní představuje kolekci úlohu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="229ca-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="229ca-112">Rozhraní představuje úlohu brány přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="229ca-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="229ca-113">Rozhraní představuje vstupně-výstupních operací vlákno úlohy nebo úlohu dokončení port přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="229ca-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="229ca-114">Rozhraní představuje úlohu časovače vláken.</span><span class="sxs-lookup"><span data-stu-id="229ca-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="229ca-115">Rozhraní představuje úlohu čekání přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="229ca-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="229ca-116">Rozhraní představuje úlohu pracovní vlákno.</span><span class="sxs-lookup"><span data-stu-id="229ca-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="229ca-117">Tato úloha neznámý.</span><span class="sxs-lookup"><span data-stu-id="229ca-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="229ca-118">Rozhraní představuje úlohu uživatele.</span><span class="sxs-lookup"><span data-stu-id="229ca-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="229ca-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="229ca-119">Requirements</span></span>  
 <span data-ttu-id="229ca-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="229ca-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="229ca-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="229ca-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="229ca-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="229ca-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="229ca-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="229ca-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229ca-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="229ca-124">See Also</span></span>  
 [<span data-ttu-id="229ca-125">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="229ca-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
