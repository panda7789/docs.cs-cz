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
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133695"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="aead0-102">CorDebugThreadState – výčet</span><span class="sxs-lookup"><span data-stu-id="aead0-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="aead0-103">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="aead0-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aead0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aead0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="aead0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aead0-105">Members</span></span>  
  
|<span data-ttu-id="aead0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aead0-106">Member</span></span>|<span data-ttu-id="aead0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aead0-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="aead0-108">Vlákno funguje volně, pokud nedojde k události ladění.</span><span class="sxs-lookup"><span data-stu-id="aead0-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="aead0-109">Vlákno nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="aead0-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aead0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aead0-110">Remarks</span></span>  
 <span data-ttu-id="aead0-111">Ladicí program používá výčet `CorDebugThreadState` k řízení provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="aead0-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="aead0-112">Stav vlákna lze nastavit pomocí metody [ICorDebugThread:: SetDebugState –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) nebo [ICorDebugController:: SetAllThreadsDebugState –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aead0-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="aead0-113">Zpětné volání, které je poskytované [hostujícímu rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md) , povoluje pumpování zpráv, takže stav přerušeno není potřeba.</span><span class="sxs-lookup"><span data-stu-id="aead0-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aead0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aead0-114">Requirements</span></span>  
 <span data-ttu-id="aead0-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aead0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aead0-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aead0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aead0-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aead0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aead0-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aead0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aead0-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aead0-119">See also</span></span>

- [<span data-ttu-id="aead0-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="aead0-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
