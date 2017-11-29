---
title: "CorDebugExceptionObjectStackFrame – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="59ef8-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="59ef8-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="59ef8-103">Představuje zásobníku rámce informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="59ef8-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ef8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ef8-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="59ef8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="59ef8-105">Members</span></span>  
  
|<span data-ttu-id="59ef8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="59ef8-106">Member</span></span>|<span data-ttu-id="59ef8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="59ef8-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="59ef8-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="59ef8-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="59ef8-109">Hodnota ukazatel instrukce (EIP nebo RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="59ef8-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="59ef8-110">Metoda token pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="59ef8-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="59ef8-111">Hodnota, která určuje, zda rámečku je poslední snímek v cizí výjimek.</span><span class="sxs-lookup"><span data-stu-id="59ef8-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ef8-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59ef8-112">Remarks</span></span>  
 <span data-ttu-id="59ef8-113">Volající musí uvolnit má ukazatel na objekt ICorDebugModule, jakmile se už používá.</span><span class="sxs-lookup"><span data-stu-id="59ef8-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ef8-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59ef8-114">Requirements</span></span>  
 <span data-ttu-id="59ef8-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ef8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ef8-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59ef8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ef8-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59ef8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ef8-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ef8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ef8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="59ef8-119">See Also</span></span>  
 [<span data-ttu-id="59ef8-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="59ef8-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="59ef8-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="59ef8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
