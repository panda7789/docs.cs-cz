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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173079"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="76829-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="76829-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="76829-103">Představuje zásobník snímků informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="76829-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76829-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76829-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="76829-105">Členové</span><span class="sxs-lookup"><span data-stu-id="76829-105">Members</span></span>  
  
|<span data-ttu-id="76829-106">Člen</span><span class="sxs-lookup"><span data-stu-id="76829-106">Member</span></span>|<span data-ttu-id="76829-107">Popis</span><span class="sxs-lookup"><span data-stu-id="76829-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="76829-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="76829-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="76829-109">Hodnota ukazatele na instrukci (EIP nebo RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="76829-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="76829-110">Token metody pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="76829-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="76829-111">Hodnota, která určuje, zda rámec je příkaz posledního rámce cizí výjimky.</span><span class="sxs-lookup"><span data-stu-id="76829-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76829-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76829-112">Remarks</span></span>  
 <span data-ttu-id="76829-113">Volající musí uvolnit ukazatel na objekt ICorDebugModule, jakmile se už používá.</span><span class="sxs-lookup"><span data-stu-id="76829-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76829-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76829-114">Requirements</span></span>  
 <span data-ttu-id="76829-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76829-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76829-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76829-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76829-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76829-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76829-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76829-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76829-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76829-119">See also</span></span>

- [<span data-ttu-id="76829-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="76829-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="76829-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="76829-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
