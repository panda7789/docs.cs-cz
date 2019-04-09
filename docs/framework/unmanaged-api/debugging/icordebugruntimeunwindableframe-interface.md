---
title: ICorDebugRuntimeUnwindableFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf6bc73683a6c37ceaaffc635a58803b71c3b6cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134196"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="98a6f-102">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98a6f-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="98a6f-103">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="98a6f-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a6f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98a6f-104">Remarks</span></span>  
 `ICorDebugRuntimeUnwindableFrame` <span data-ttu-id="98a6f-105">je specializované verze icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="98a6f-105">is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="98a6f-106">Používá se nespravované metody, které vyžadují modul runtime k uvolnění rámce aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="98a6f-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="98a6f-107">Existující odvíjení konvence nefungují, protože nepoužívají kód zkompilovaný kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="98a6f-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="98a6f-108">Pokud ladicí program zobrazí neuvolnitelných rámce, měla by používat [icordebugstackwalk::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metody k provedení operace unwind ji, ale měli provést kontrolu, samotného.</span><span class="sxs-lookup"><span data-stu-id="98a6f-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="98a6f-109">Když ladicí program dostane `ICorDebugRuntimeUnwindableFrame`, může zavolat [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody k získání kontextu rámce.</span><span class="sxs-lookup"><span data-stu-id="98a6f-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a6f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98a6f-110">Requirements</span></span>  
 <span data-ttu-id="98a6f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98a6f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a6f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a6f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a6f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a6f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="98a6f-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="98a6f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="98a6f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98a6f-115">See also</span></span>

- [<span data-ttu-id="98a6f-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98a6f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="98a6f-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="98a6f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
