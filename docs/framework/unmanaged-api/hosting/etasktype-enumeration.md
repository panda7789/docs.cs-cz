---
title: ETaskType – výčet
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493315"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="10157-102">ETaskType – výčet</span><span class="sxs-lookup"><span data-stu-id="10157-102">ETaskType Enumeration</span></span>
<span data-ttu-id="10157-103">Obsahuje hodnoty, které určují typ úlohy, který je reprezentován buď [ICLRTask](iclrtask-interface.md) nebo rozhraním [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="10157-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10157-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10157-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="10157-105">Členové</span><span class="sxs-lookup"><span data-stu-id="10157-105">Members</span></span>  
  
|<span data-ttu-id="10157-106">Člen</span><span class="sxs-lookup"><span data-stu-id="10157-106">Member</span></span>|<span data-ttu-id="10157-107">Description</span><span class="sxs-lookup"><span data-stu-id="10157-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="10157-108">Rozhraní představuje úlohu uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="10157-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="10157-109">Rozhraní představuje úlohu pomocníka ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="10157-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="10157-110">Rozhraní představuje úlohu finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="10157-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="10157-111">Rozhraní představuje úlohu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="10157-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="10157-112">Rozhraní představuje úlohu vlákna brány.</span><span class="sxs-lookup"><span data-stu-id="10157-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="10157-113">Rozhraní představuje úlohu vstupně-výstupního vlákna nebo úlohu vlákna portu pro dokončení.</span><span class="sxs-lookup"><span data-stu-id="10157-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="10157-114">Rozhraní představuje úlohu vlákna časovače.</span><span class="sxs-lookup"><span data-stu-id="10157-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="10157-115">Rozhraní představuje úlohu vlákna čekání.</span><span class="sxs-lookup"><span data-stu-id="10157-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="10157-116">Rozhraní představuje úlohu pracovního vlákna.</span><span class="sxs-lookup"><span data-stu-id="10157-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="10157-117">Úloha je neznámá.</span><span class="sxs-lookup"><span data-stu-id="10157-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="10157-118">Rozhraní představuje úkol uživatele.</span><span class="sxs-lookup"><span data-stu-id="10157-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10157-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10157-119">Requirements</span></span>  
 <span data-ttu-id="10157-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10157-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10157-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10157-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10157-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="10157-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10157-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10157-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10157-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10157-124">See also</span></span>

- [<span data-ttu-id="10157-125">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="10157-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
