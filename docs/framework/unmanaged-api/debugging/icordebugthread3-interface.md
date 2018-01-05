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
ms.workload: dotnet
ms.openlocfilehash: 6cfb3267637210567f3df9fa08bb75135dc585ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="87cf4-102">ICorDebugThread3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87cf4-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="87cf4-103">Představuje vstupní bod do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) a odpovídající rozhraní.</span><span class="sxs-lookup"><span data-stu-id="87cf4-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87cf4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="87cf4-104">Methods</span></span>  
  
|<span data-ttu-id="87cf4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="87cf4-105">Method</span></span>|<span data-ttu-id="87cf4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="87cf4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87cf4-107">CreateStackWalk – metoda</span><span class="sxs-lookup"><span data-stu-id="87cf4-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="87cf4-108">Vytvoří [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objekt, pro jehož zásobníku chcete unwind vlákno.</span><span class="sxs-lookup"><span data-stu-id="87cf4-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="87cf4-109">GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="87cf4-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="87cf4-110">Vrátí pole interní rámce ([icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objekty) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="87cf4-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87cf4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87cf4-111">Remarks</span></span>  
 <span data-ttu-id="87cf4-112">`ICorDebugThread3`je logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="87cf4-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87cf4-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="87cf4-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87cf4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87cf4-114">Requirements</span></span>  
 <span data-ttu-id="87cf4-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87cf4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87cf4-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87cf4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87cf4-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87cf4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87cf4-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87cf4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cf4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="87cf4-119">See Also</span></span>  
 [<span data-ttu-id="87cf4-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="87cf4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="87cf4-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="87cf4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
