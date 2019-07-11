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
ms.openlocfilehash: 8bda8079cff8f5e8fafade03a02c3dfe8798c5ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740769"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="fbeef-102">COR_DEBUG_STEP_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="fbeef-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="fbeef-103">Obsahuje informace o posunu pro celou řadu kódu.</span><span class="sxs-lookup"><span data-stu-id="fbeef-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="fbeef-104">Tato struktura je používán [icordebugstepper::steprange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fbeef-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbeef-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbeef-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="fbeef-106">Členové</span><span class="sxs-lookup"><span data-stu-id="fbeef-106">Members</span></span>  
  
|<span data-ttu-id="fbeef-107">Člen</span><span class="sxs-lookup"><span data-stu-id="fbeef-107">Member</span></span>|<span data-ttu-id="fbeef-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fbeef-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="fbeef-109">Posun začátek rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fbeef-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="fbeef-110">Posun konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fbeef-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbeef-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbeef-111">Requirements</span></span>  
 <span data-ttu-id="fbeef-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbeef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbeef-113">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="fbeef-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fbeef-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbeef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbeef-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbeef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbeef-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fbeef-116">See also</span></span>

- [<span data-ttu-id="fbeef-117">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="fbeef-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="fbeef-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="fbeef-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="fbeef-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="fbeef-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
