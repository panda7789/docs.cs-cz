---
title: COR_DEBUG_STEP_RANGE – struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5809221f2f31bc725c6a62fa5f8f91822f1c157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407224"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="1ca68-102">COR_DEBUG_STEP_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="1ca68-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="1ca68-103">Obsahuje informace o posunu pro řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="1ca68-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="1ca68-104">Tato struktura je používán [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="1ca68-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca68-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ca68-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="1ca68-106">Členové</span><span class="sxs-lookup"><span data-stu-id="1ca68-106">Members</span></span>  
  
|<span data-ttu-id="1ca68-107">Člen</span><span class="sxs-lookup"><span data-stu-id="1ca68-107">Member</span></span>|<span data-ttu-id="1ca68-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1ca68-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="1ca68-109">Posun na začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1ca68-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="1ca68-110">Posun konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1ca68-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ca68-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ca68-111">Requirements</span></span>  
 <span data-ttu-id="1ca68-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca68-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca68-113">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="1ca68-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1ca68-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ca68-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ca68-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca68-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca68-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ca68-116">See Also</span></span>  
 [<span data-ttu-id="1ca68-117">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1ca68-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="1ca68-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="1ca68-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="1ca68-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="1ca68-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
