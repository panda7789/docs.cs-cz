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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378711"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="b018e-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b018e-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="b018e-103">Poskytuje vstupní bod pro [ICorDebugStackWalk](icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b018e-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b018e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b018e-104">Methods</span></span>  
  
|<span data-ttu-id="b018e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b018e-105">Method</span></span>|<span data-ttu-id="b018e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b018e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b018e-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="b018e-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="b018e-108">Vytvoří objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) pro vlákno, jehož zásobník chcete vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="b018e-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="b018e-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="b018e-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="b018e-110">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b018e-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b018e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b018e-111">Remarks</span></span>  
 <span data-ttu-id="b018e-112">`ICorDebugThread3`je logickým rozšířením rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b018e-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b018e-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b018e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b018e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b018e-114">Requirements</span></span>  
 <span data-ttu-id="b018e-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b018e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b018e-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b018e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b018e-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b018e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b018e-118">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b018e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b018e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b018e-119">See also</span></span>

- [<span data-ttu-id="b018e-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b018e-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b018e-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="b018e-121">Debugging</span></span>](index.md)
