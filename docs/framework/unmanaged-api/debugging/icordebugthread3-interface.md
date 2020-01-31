---
title: ICorDebugThread3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791381"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="f035a-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f035a-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="f035a-103">Poskytuje vstupní bod pro [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f035a-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f035a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f035a-104">Methods</span></span>  
  
|<span data-ttu-id="f035a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f035a-105">Method</span></span>|<span data-ttu-id="f035a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f035a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f035a-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="f035a-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="f035a-108">Vytvoří objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="f035a-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="f035a-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="f035a-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="f035a-110">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f035a-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f035a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f035a-111">Remarks</span></span>  
 <span data-ttu-id="f035a-112">`ICorDebugThread3` je logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f035a-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f035a-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f035a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f035a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f035a-114">Requirements</span></span>  
 <span data-ttu-id="f035a-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f035a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f035a-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f035a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f035a-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f035a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f035a-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f035a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f035a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f035a-119">See also</span></span>

- [<span data-ttu-id="f035a-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f035a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f035a-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="f035a-121">Debugging</span></span>](index.md)
