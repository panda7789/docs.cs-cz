---
title: "CorDebugBlockingReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 505a83f15d5056b0280af31d372623530d6e66ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="fb9ba-102">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="fb9ba-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="fb9ba-103">Určuje z důvodů, proč může zablokování vlákna na daný objekt.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb9ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb9ba-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="fb9ba-105">Členové</span><span class="sxs-lookup"><span data-stu-id="fb9ba-105">Members</span></span>  
  
|<span data-ttu-id="fb9ba-106">Člen</span><span class="sxs-lookup"><span data-stu-id="fb9ba-106">Member</span></span>|<span data-ttu-id="fb9ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fb9ba-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="fb9ba-108">Pouze interní použití.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="fb9ba-109">Vlákno se pokouší získat důležité oddíl, který je přidružen monitorování zámek objektu.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="fb9ba-110">Obvykle k tomu dojde při volání jednoho z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="fb9ba-111">Vlákno čeká na událost, která souvisí s monitorování zámek objektu.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="fb9ba-112">Obvykle k tomu dojde při volání jednoho z <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb9ba-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb9ba-113">Remarks</span></span>  
 <span data-ttu-id="fb9ba-114">Když `BLOCKING_MONITOR_CRITICAL_SECTION` nebo `BLOCKING_MONITOR_EVENT` člen se používá v [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktura, `pBlockingObject` člen struktura ukazuje na rozhraní "ICorDebugValue", který představuje objekt, který jste právě zadali .</span><span class="sxs-lookup"><span data-stu-id="fb9ba-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="fb9ba-115">Je také zaručit implementovat [icordebugheapvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb9ba-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb9ba-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb9ba-116">Requirements</span></span>  
 <span data-ttu-id="fb9ba-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb9ba-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb9ba-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb9ba-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb9ba-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb9ba-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb9ba-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb9ba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9ba-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb9ba-121">See Also</span></span>  
 [<span data-ttu-id="fb9ba-122">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="fb9ba-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="fb9ba-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="fb9ba-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
