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
ms.openlocfilehash: 9c22ca47a606da0949529cf55655bbcde19cb5c9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795661"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="4ad4a-102">CorDebugThreadState – výčet</span><span class="sxs-lookup"><span data-stu-id="4ad4a-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="4ad4a-103">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="4ad4a-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ad4a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="4ad4a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4ad4a-105">Members</span></span>  
  
|<span data-ttu-id="4ad4a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4ad4a-106">Member</span></span>|<span data-ttu-id="4ad4a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4ad4a-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="4ad4a-108">Vlákno funguje volně, pokud nedojde k události ladění.</span><span class="sxs-lookup"><span data-stu-id="4ad4a-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="4ad4a-109">Vlákno nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="4ad4a-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad4a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ad4a-110">Remarks</span></span>  
 <span data-ttu-id="4ad4a-111">Ladicí program používá `CorDebugThreadState` výčet k řízení provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="4ad4a-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="4ad4a-112">Stav vlákna lze nastavit pomocí metody [ICorDebugThread:: SetDebugState –](icordebugthread-setdebugstate-method.md) nebo [ICorDebugController:: SetAllThreadsDebugState –](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4ad4a-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="4ad4a-113">Zpětné volání, které je poskytované [hostujícímu rozhraní API](../hosting/index.md) , povoluje pumpování zpráv, takže stav přerušeno není potřeba.</span><span class="sxs-lookup"><span data-stu-id="4ad4a-113">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ad4a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ad4a-114">Requirements</span></span>  
 <span data-ttu-id="4ad4a-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ad4a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ad4a-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ad4a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ad4a-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4ad4a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ad4a-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ad4a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad4a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ad4a-119">See also</span></span>

- [<span data-ttu-id="4ad4a-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="4ad4a-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
