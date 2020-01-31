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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791921"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="123ac-102">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="123ac-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="123ac-103">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="123ac-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="123ac-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="123ac-104">Remarks</span></span>  
 <span data-ttu-id="123ac-105">`ICorDebugRuntimeUnwindableFrame` je specializovaná verze rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="123ac-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="123ac-106">Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku.</span><span class="sxs-lookup"><span data-stu-id="123ac-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="123ac-107">Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT.</span><span class="sxs-lookup"><span data-stu-id="123ac-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="123ac-108">Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu.</span><span class="sxs-lookup"><span data-stu-id="123ac-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="123ac-109">Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame`, může volat metodu [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.</span><span class="sxs-lookup"><span data-stu-id="123ac-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="123ac-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="123ac-110">Requirements</span></span>  
 <span data-ttu-id="123ac-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="123ac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="123ac-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="123ac-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="123ac-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="123ac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="123ac-114">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="123ac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123ac-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="123ac-115">See also</span></span>

- [<span data-ttu-id="123ac-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="123ac-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="123ac-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="123ac-117">Debugging</span></span>](index.md)
