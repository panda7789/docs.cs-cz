---
title: "ICorDebugThread3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed505cacc5286d27bc9a94eaa192dc6b889eb525
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="15bc8-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15bc8-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="15bc8-103">Představuje vstupní bod do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15bc8-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15bc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="15bc8-104">Methods</span></span>  
  
|<span data-ttu-id="15bc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="15bc8-105">Method</span></span>|<span data-ttu-id="15bc8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="15bc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15bc8-107">Createstackwalk – metoda</span><span class="sxs-lookup"><span data-stu-id="15bc8-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="15bc8-108">Vytvoří [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objekt, pro jehož zásobníku chcete unwind vlákno.</span><span class="sxs-lookup"><span data-stu-id="15bc8-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="15bc8-109">Getactiveinternalframes – metoda</span><span class="sxs-lookup"><span data-stu-id="15bc8-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="15bc8-110">Vrátí pole interní rámce ([icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objekty) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="15bc8-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15bc8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15bc8-111">Remarks</span></span>  
 <span data-ttu-id="15bc8-112">`ICorDebugThread3`je logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="15bc8-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15bc8-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="15bc8-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15bc8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15bc8-114">Requirements</span></span>  
 <span data-ttu-id="15bc8-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15bc8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15bc8-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15bc8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15bc8-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15bc8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15bc8-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15bc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bc8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="15bc8-119">See Also</span></span>  
 [<span data-ttu-id="15bc8-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="15bc8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="15bc8-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="15bc8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
