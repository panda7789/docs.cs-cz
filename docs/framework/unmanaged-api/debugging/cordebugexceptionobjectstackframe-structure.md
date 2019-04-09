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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173079"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="07ccb-102">CorDebugExceptionObjectStackFrame – struktura</span><span class="sxs-lookup"><span data-stu-id="07ccb-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="07ccb-103">Představuje zásobník snímků informace z objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="07ccb-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ccb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07ccb-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="07ccb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="07ccb-105">Members</span></span>  
  
|<span data-ttu-id="07ccb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="07ccb-106">Member</span></span>|<span data-ttu-id="07ccb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="07ccb-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="07ccb-108">Ukazatel na objekt ICorDebugModule pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="07ccb-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="07ccb-109">Hodnota ukazatele na instrukci (EIP nebo RIP) pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="07ccb-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="07ccb-110">Token metody pro aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="07ccb-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="07ccb-111">Hodnota, která určuje, zda rámec je příkaz posledního rámce cizí výjimky.</span><span class="sxs-lookup"><span data-stu-id="07ccb-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07ccb-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07ccb-112">Remarks</span></span>  
 <span data-ttu-id="07ccb-113">Volající musí uvolnit ukazatel na objekt ICorDebugModule, jakmile se už používá.</span><span class="sxs-lookup"><span data-stu-id="07ccb-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ccb-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07ccb-114">Requirements</span></span>  
 <span data-ttu-id="07ccb-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ccb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ccb-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07ccb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07ccb-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07ccb-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="07ccb-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="07ccb-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07ccb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07ccb-119">See also</span></span>

- [<span data-ttu-id="07ccb-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="07ccb-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="07ccb-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="07ccb-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
