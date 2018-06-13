---
title: CorDebugExceptionObjectStackFrame – struktura
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48b15429d40d3a69db52615592fc1697f385d319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403728"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="a0c54-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="a0c54-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="a0c54-103">Představuje zásobníku rámce informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="a0c54-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0c54-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="a0c54-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a0c54-105">Members</span></span>  
  
|<span data-ttu-id="a0c54-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a0c54-106">Member</span></span>|<span data-ttu-id="a0c54-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a0c54-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="a0c54-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="a0c54-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="a0c54-109">Hodnota ukazatel instrukce (EIP nebo RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="a0c54-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="a0c54-110">Metoda token pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="a0c54-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="a0c54-111">Hodnota, která určuje, zda rámečku je poslední snímek v cizí výjimek.</span><span class="sxs-lookup"><span data-stu-id="a0c54-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c54-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c54-112">Remarks</span></span>  
 <span data-ttu-id="a0c54-113">Volající musí uvolnit má ukazatel na objekt ICorDebugModule, jakmile se už používá.</span><span class="sxs-lookup"><span data-stu-id="a0c54-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c54-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0c54-114">Requirements</span></span>  
 <span data-ttu-id="a0c54-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c54-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c54-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0c54-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0c54-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0c54-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0c54-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c54-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c54-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c54-119">See Also</span></span>  
 [<span data-ttu-id="a0c54-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="a0c54-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="a0c54-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="a0c54-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
