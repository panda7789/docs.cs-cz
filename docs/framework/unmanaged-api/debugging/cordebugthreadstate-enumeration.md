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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efb7f5b8e63742471123a0e0a38cebe605f3696f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092445"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="b14fc-102">CorDebugThreadState – výčet</span><span class="sxs-lookup"><span data-stu-id="b14fc-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="b14fc-103">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b14fc-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b14fc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="b14fc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b14fc-105">Members</span></span>  
  
|<span data-ttu-id="b14fc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b14fc-106">Member</span></span>|<span data-ttu-id="b14fc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b14fc-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="b14fc-108">Vlákno se spustí bez omezení, pokud dojde k události ladění.</span><span class="sxs-lookup"><span data-stu-id="b14fc-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="b14fc-109">Vlákno nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="b14fc-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b14fc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b14fc-110">Remarks</span></span>  
 <span data-ttu-id="b14fc-111">Ladicí program používá `CorDebugThreadState` výčet k řízení provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="b14fc-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="b14fc-112">Stav vlákna lze nastavit pomocí [icordebugthread::setdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) nebo [icordebugcontroller::setallthreadsdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b14fc-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="b14fc-113">Zpětné volání k dispozici na [hostování API](../../../../docs/framework/unmanaged-api/hosting/index.md) umožňuje – čerpání zpráv, takže není potřeba přerušené stavu.</span><span class="sxs-lookup"><span data-stu-id="b14fc-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b14fc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b14fc-114">Requirements</span></span>  
 <span data-ttu-id="b14fc-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b14fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b14fc-116">**Záhlaví:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="b14fc-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="b14fc-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b14fc-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b14fc-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b14fc-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b14fc-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b14fc-119">See also</span></span>

- [<span data-ttu-id="b14fc-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b14fc-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
