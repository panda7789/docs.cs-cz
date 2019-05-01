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
ms.openlocfilehash: 5a4cd4d353c22921ed3dba1dc08fe2cee7e429f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996317"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="201ea-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="201ea-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="201ea-103">Představuje zásobník snímků informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="201ea-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="201ea-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="201ea-105">Členové</span><span class="sxs-lookup"><span data-stu-id="201ea-105">Members</span></span>  
  
|<span data-ttu-id="201ea-106">Člen</span><span class="sxs-lookup"><span data-stu-id="201ea-106">Member</span></span>|<span data-ttu-id="201ea-107">Popis</span><span class="sxs-lookup"><span data-stu-id="201ea-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="201ea-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="201ea-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="201ea-109">Hodnota ukazatele na instrukci (EIP nebo RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="201ea-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="201ea-110">Token metody pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="201ea-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="201ea-111">Hodnota, která určuje, zda rámec je příkaz posledního rámce cizí výjimky.</span><span class="sxs-lookup"><span data-stu-id="201ea-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="201ea-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="201ea-112">Remarks</span></span>  
 <span data-ttu-id="201ea-113">Volající musí uvolnit ukazatel na objekt ICorDebugModule, jakmile se už používá.</span><span class="sxs-lookup"><span data-stu-id="201ea-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201ea-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="201ea-114">Requirements</span></span>  
 <span data-ttu-id="201ea-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="201ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201ea-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="201ea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="201ea-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="201ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="201ea-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201ea-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="201ea-119">See also</span></span>

- [<span data-ttu-id="201ea-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="201ea-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="201ea-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="201ea-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
