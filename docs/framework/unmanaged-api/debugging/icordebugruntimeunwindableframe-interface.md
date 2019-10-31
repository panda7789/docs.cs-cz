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
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131889"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="2858d-102">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2858d-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="2858d-103">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="2858d-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2858d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2858d-104">Remarks</span></span>  
 <span data-ttu-id="2858d-105">`ICorDebugRuntimeUnwindableFrame` je specializovaná verze rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2858d-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="2858d-106">Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2858d-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="2858d-107">Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT.</span><span class="sxs-lookup"><span data-stu-id="2858d-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="2858d-108">Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu.</span><span class="sxs-lookup"><span data-stu-id="2858d-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="2858d-109">Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame`, může volat metodu [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.</span><span class="sxs-lookup"><span data-stu-id="2858d-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2858d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2858d-110">Requirements</span></span>  
 <span data-ttu-id="2858d-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2858d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2858d-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2858d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2858d-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2858d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2858d-114">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2858d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2858d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2858d-115">See also</span></span>

- [<span data-ttu-id="2858d-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2858d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2858d-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="2858d-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
