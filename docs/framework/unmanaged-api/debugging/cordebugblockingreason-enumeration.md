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
ms.openlocfilehash: 54652727b4684d71068a19eb5eeb2e862f413f25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609253"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="3943c-102">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="3943c-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="3943c-103">Určuje důvody, proč může zablokování vlákna na daný objekt.</span><span class="sxs-lookup"><span data-stu-id="3943c-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3943c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3943c-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="3943c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3943c-105">Members</span></span>  
  
|<span data-ttu-id="3943c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3943c-106">Member</span></span>|<span data-ttu-id="3943c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3943c-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="3943c-108">Pouze pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="3943c-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="3943c-109">Vlákno se pokouší získat kritický oddíl, který je přidružený k uzamčení monitoru objektu.</span><span class="sxs-lookup"><span data-stu-id="3943c-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="3943c-110">Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3943c-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="3943c-111">Vlákno čeká na událost, která je přidružený k uzamčení monitoru objektu.</span><span class="sxs-lookup"><span data-stu-id="3943c-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="3943c-112">Obvykle to nastane, pokud voláním <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.</span><span class="sxs-lookup"><span data-stu-id="3943c-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3943c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3943c-113">Remarks</span></span>  
 <span data-ttu-id="3943c-114">Při `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` člena se používá v [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury, `pBlockingObject` členem struktury odkazuje na rozhraní "ICorDebugValue", který představuje objekt, který je zadání .</span><span class="sxs-lookup"><span data-stu-id="3943c-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="3943c-115">Je také zaručeno, že k implementaci [icordebugheapvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3943c-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3943c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3943c-116">Requirements</span></span>  
 <span data-ttu-id="3943c-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3943c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3943c-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3943c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3943c-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3943c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3943c-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3943c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3943c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3943c-121">See also</span></span>

- [<span data-ttu-id="3943c-122">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="3943c-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="3943c-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="3943c-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
