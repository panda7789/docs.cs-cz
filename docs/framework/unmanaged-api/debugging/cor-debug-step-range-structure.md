---
title: "COR_DEBUG_STEP_RANGE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27b1b7b26ea788683f9b322306c55a4b3945f342
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="9d199-102">COR_DEBUG_STEP_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="9d199-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="9d199-103">Obsahuje informace o posunu pro řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="9d199-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="9d199-104">Tato struktura je používán [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="9d199-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d199-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d199-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="9d199-106">Členové</span><span class="sxs-lookup"><span data-stu-id="9d199-106">Members</span></span>  
  
|<span data-ttu-id="9d199-107">Člen</span><span class="sxs-lookup"><span data-stu-id="9d199-107">Member</span></span>|<span data-ttu-id="9d199-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9d199-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="9d199-109">Posun na začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="9d199-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="9d199-110">Posun konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="9d199-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d199-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d199-111">Requirements</span></span>  
 <span data-ttu-id="9d199-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d199-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d199-113">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="9d199-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="9d199-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d199-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d199-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d199-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d199-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d199-116">See Also</span></span>  
 [<span data-ttu-id="9d199-117">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="9d199-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="9d199-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="9d199-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9d199-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="9d199-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
