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
ms.openlocfilehash: 206e4fb232f4786a76525d24aa379b25d6d2f71d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099349"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="1d353-102">COR_DEBUG_STEP_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="1d353-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="1d353-103">Obsahuje informace o posunu pro rozsah kódu.</span><span class="sxs-lookup"><span data-stu-id="1d353-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="1d353-104">Tato struktura je používána metodou [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1d353-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d353-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d353-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="1d353-106">Členové</span><span class="sxs-lookup"><span data-stu-id="1d353-106">Members</span></span>  
  
|<span data-ttu-id="1d353-107">Člen</span><span class="sxs-lookup"><span data-stu-id="1d353-107">Member</span></span>|<span data-ttu-id="1d353-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1d353-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="1d353-109">Posun začátku rozsahu</span><span class="sxs-lookup"><span data-stu-id="1d353-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="1d353-110">Posun konce rozsahu</span><span class="sxs-lookup"><span data-stu-id="1d353-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d353-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1d353-111">Requirements</span></span>  
 <span data-ttu-id="1d353-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d353-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d353-113">**Hlavička:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="1d353-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="1d353-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1d353-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d353-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d353-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d353-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d353-116">See also</span></span>

- [<span data-ttu-id="1d353-117">StepRange – metoda</span><span class="sxs-lookup"><span data-stu-id="1d353-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="1d353-118">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="1d353-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1d353-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="1d353-119">Debugging</span></span>](index.md)
