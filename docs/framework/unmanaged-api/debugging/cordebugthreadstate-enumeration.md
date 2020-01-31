---
title: CorDebugThreadState – výčet
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 69a8aabd1d79bb9bb4248259c99124ce50677600
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789247"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="e28e2-102">CorDebugThreadState – výčet</span><span class="sxs-lookup"><span data-stu-id="e28e2-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="e28e2-103">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e28e2-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e28e2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="e28e2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e28e2-105">Members</span></span>  
  
|<span data-ttu-id="e28e2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e28e2-106">Member</span></span>|<span data-ttu-id="e28e2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e28e2-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="e28e2-108">Vlákno funguje volně, pokud nedojde k události ladění.</span><span class="sxs-lookup"><span data-stu-id="e28e2-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="e28e2-109">Vlákno nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="e28e2-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e28e2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e28e2-110">Remarks</span></span>  
 <span data-ttu-id="e28e2-111">Ladicí program používá výčet `CorDebugThreadState` k řízení provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="e28e2-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="e28e2-112">Stav vlákna lze nastavit pomocí metody [ICorDebugThread:: SetDebugState –](icordebugthread-setdebugstate-method.md) nebo [ICorDebugController:: SetAllThreadsDebugState –](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e28e2-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="e28e2-113">Zpětné volání, které je poskytované [hostujícímu rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md) , povoluje pumpování zpráv, takže stav přerušeno není potřeba.</span><span class="sxs-lookup"><span data-stu-id="e28e2-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28e2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e28e2-114">Requirements</span></span>  
 <span data-ttu-id="e28e2-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e28e2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28e2-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e28e2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e28e2-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e28e2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e28e2-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e28e2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28e2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e28e2-119">See also</span></span>

- [<span data-ttu-id="e28e2-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="e28e2-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
