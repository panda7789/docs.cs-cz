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
ms.openlocfilehash: a7b0608e85411844828cebea34c0ce5ef5b1bd11
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379388"
---
# <a name="icordebugruntimeunwindableframe-interface"></a><span data-ttu-id="32a7a-102">ICorDebugRuntimeUnwindableFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32a7a-102">ICorDebugRuntimeUnwindableFrame Interface</span></span>
<span data-ttu-id="32a7a-103">Poskytuje podporu pro nespravované metody, které vyžadují modul CLR k uvolnění rámce.</span><span class="sxs-lookup"><span data-stu-id="32a7a-103">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32a7a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32a7a-104">Remarks</span></span>  
 <span data-ttu-id="32a7a-105">`ICorDebugRuntimeUnwindableFrame`je specializovaná verze rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="32a7a-105">`ICorDebugRuntimeUnwindableFrame` is a specialized version of the ICorDebugFrame interface.</span></span> <span data-ttu-id="32a7a-106">Používá je nespravované metody, které vyžadují, aby modul runtime odvíjí snímek v aktuálním zásobníku.</span><span class="sxs-lookup"><span data-stu-id="32a7a-106">It is used by unmanaged methods that require the runtime to unwind a frame on the current stack.</span></span> <span data-ttu-id="32a7a-107">Existující konvence unwindy nefungují, protože nepoužívají kód zkompilovaný JIT.</span><span class="sxs-lookup"><span data-stu-id="32a7a-107">Existing unwinding conventions do not work, because they do not use JIT-compiled code.</span></span> <span data-ttu-id="32a7a-108">Pokud se ladicí program dohlíží na nejenom nejenomný snímek, měl by použít metodu [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) k jejímu unwind, ale měla by provádět kontrolu.</span><span class="sxs-lookup"><span data-stu-id="32a7a-108">When the debugger sees an unwindable frame, it should use the [ICorDebugStackWalk::Next](icordebugstackwalk-next-method.md) method to unwind it, but it should perform inspection itself.</span></span> <span data-ttu-id="32a7a-109">Když ladicí program obdrží `ICorDebugRuntimeUnwindableFrame` , může zavolat metodu [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) pro načtení kontextu rámce.</span><span class="sxs-lookup"><span data-stu-id="32a7a-109">When the debugger receives an `ICorDebugRuntimeUnwindableFrame`, it can call the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method to retrieve the context of the frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a7a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32a7a-110">Requirements</span></span>  
 <span data-ttu-id="32a7a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a7a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a7a-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32a7a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32a7a-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32a7a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a7a-114">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a7a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a7a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="32a7a-115">See also</span></span>

- [<span data-ttu-id="32a7a-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="32a7a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="32a7a-117">Ladění</span><span class="sxs-lookup"><span data-stu-id="32a7a-117">Debugging</span></span>](index.md)
