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
ms.openlocfilehash: faa2082d31c5fa47b87e2238017066b477fdc191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132175"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="b45ae-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="b45ae-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="b45ae-103">Představuje informace o snímku zásobníku z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="b45ae-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b45ae-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="b45ae-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b45ae-105">Members</span></span>  
  
|<span data-ttu-id="b45ae-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b45ae-106">Member</span></span>|<span data-ttu-id="b45ae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b45ae-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="b45ae-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="b45ae-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="b45ae-109">Hodnota ukazatele instrukce (EIP/RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="b45ae-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="b45ae-110">Token metody pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="b45ae-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="b45ae-111">Hodnota, která označuje, zda je rámec posledním snímkem v cizí výjimce.</span><span class="sxs-lookup"><span data-stu-id="b45ae-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b45ae-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b45ae-112">Remarks</span></span>  
 <span data-ttu-id="b45ae-113">Volající musí uvolnit ukazatel na objekt ICorDebugModule, jakmile se již nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b45ae-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b45ae-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b45ae-114">Requirements</span></span>  
 <span data-ttu-id="b45ae-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45ae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45ae-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b45ae-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b45ae-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b45ae-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b45ae-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45ae-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b45ae-119">See also</span></span>

- [<span data-ttu-id="b45ae-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b45ae-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b45ae-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="b45ae-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
