---
title: "CorDebugThreadState – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugThreadState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugThreadState
helpviewer_keywords: CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a5363282f2efed003238014390f50c448c529ce2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="783b5-102">CorDebugThreadState – výčet</span><span class="sxs-lookup"><span data-stu-id="783b5-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="783b5-103">Určuje stav vláken pro ladění.</span><span class="sxs-lookup"><span data-stu-id="783b5-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="783b5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="783b5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="783b5-105">Members</span></span>  
  
|<span data-ttu-id="783b5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="783b5-106">Member</span></span>|<span data-ttu-id="783b5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="783b5-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="783b5-108">Vlákno spouští volně, pokud dojde k události ladění.</span><span class="sxs-lookup"><span data-stu-id="783b5-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="783b5-109">Nelze spustit vlákno.</span><span class="sxs-lookup"><span data-stu-id="783b5-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="783b5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="783b5-110">Remarks</span></span>  
 <span data-ttu-id="783b5-111">Ladicí program používá `CorDebugThreadState` výčtu k řízení provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="783b5-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="783b5-112">Stav vlákna lze nastavit pomocí [icordebugthread::setdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) nebo [icordebugcontroller::setallthreadsdebugstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="783b5-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="783b5-113">Zpětné volání poskytnuté [hostující rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md) umožňuje čerpání zpráv, takže dojde k přerušení stavu není potřeba.</span><span class="sxs-lookup"><span data-stu-id="783b5-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="783b5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="783b5-114">Requirements</span></span>  
 <span data-ttu-id="783b5-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="783b5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="783b5-116">**Záhlaví:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="783b5-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="783b5-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="783b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="783b5-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="783b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="783b5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="783b5-119">See Also</span></span>  
 [<span data-ttu-id="783b5-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="783b5-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
