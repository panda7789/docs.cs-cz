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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740384"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="03a44-102">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="03a44-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="03a44-103">Určuje důvody, proč může zablokování vlákna na daný objekt.</span><span class="sxs-lookup"><span data-stu-id="03a44-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a44-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="03a44-105">Členové</span><span class="sxs-lookup"><span data-stu-id="03a44-105">Members</span></span>  
  
|<span data-ttu-id="03a44-106">Člen</span><span class="sxs-lookup"><span data-stu-id="03a44-106">Member</span></span>|<span data-ttu-id="03a44-107">Popis</span><span class="sxs-lookup"><span data-stu-id="03a44-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="03a44-108">Pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="03a44-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="03a44-109">Vlákno se pokouší získat kritický oddíl, který je přidružený k uzamčení monitoru objektu.</span><span class="sxs-lookup"><span data-stu-id="03a44-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="03a44-110">Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="03a44-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="03a44-111">Vlákno čeká na událost, která je přidružený k uzamčení monitoru objektu.</span><span class="sxs-lookup"><span data-stu-id="03a44-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="03a44-112">Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.</span><span class="sxs-lookup"><span data-stu-id="03a44-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a44-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03a44-113">Remarks</span></span>  
 <span data-ttu-id="03a44-114">Při `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` člena se používá v [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury, `pBlockingObject` členem struktury odkazuje na rozhraní "ICorDebugValue", který představuje objekt, který je zadání .</span><span class="sxs-lookup"><span data-stu-id="03a44-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="03a44-115">Je také zaručeno, že k implementaci [icordebugheapvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="03a44-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a44-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03a44-116">Requirements</span></span>  
 <span data-ttu-id="03a44-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a44-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a44-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03a44-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03a44-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03a44-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03a44-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a44-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03a44-121">See also</span></span>

- [<span data-ttu-id="03a44-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="03a44-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="03a44-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="03a44-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
