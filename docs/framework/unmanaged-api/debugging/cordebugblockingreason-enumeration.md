---
title: CorDebugBlockingReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: bc488e55bf64468eb62e2dc6eaedca62ebde3310
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098989"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="39341-102">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="39341-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="39341-103">Určuje důvody, proč se vlákno může v daném objektu zablokovat.</span><span class="sxs-lookup"><span data-stu-id="39341-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39341-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="39341-105">Členové</span><span class="sxs-lookup"><span data-stu-id="39341-105">Members</span></span>  
  
|<span data-ttu-id="39341-106">Člen</span><span class="sxs-lookup"><span data-stu-id="39341-106">Member</span></span>|<span data-ttu-id="39341-107">Popis</span><span class="sxs-lookup"><span data-stu-id="39341-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="39341-108">Pouze interní použití.</span><span class="sxs-lookup"><span data-stu-id="39341-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="39341-109">Vlákno se snaží získat kritickou část, která je přidružena k zámku monitoru u objektu.</span><span class="sxs-lookup"><span data-stu-id="39341-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="39341-110">K tomu obvykle dochází při volání jedné z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>ch metod.</span><span class="sxs-lookup"><span data-stu-id="39341-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="39341-111">Vlákno čeká na událost, která je přidružena k zámku monitoru pro objekt.</span><span class="sxs-lookup"><span data-stu-id="39341-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="39341-112">Obvykle k tomu dochází, když zavoláte jednu z <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` metod.</span><span class="sxs-lookup"><span data-stu-id="39341-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39341-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39341-113">Remarks</span></span>  
 <span data-ttu-id="39341-114">Když je člen `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` použit ve struktuře [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , odkazuje `pBlockingObject` člen struktury na rozhraní "ICorDebugValue", které představuje objekt, který je právě zadán.</span><span class="sxs-lookup"><span data-stu-id="39341-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="39341-115">Je také zaručena implementace rozhraní [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="39341-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39341-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39341-116">Requirements</span></span>  
 <span data-ttu-id="39341-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39341-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39341-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="39341-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39341-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="39341-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39341-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39341-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39341-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39341-121">See also</span></span>

- [<span data-ttu-id="39341-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="39341-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="39341-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="39341-123">Debugging</span></span>](index.md)
