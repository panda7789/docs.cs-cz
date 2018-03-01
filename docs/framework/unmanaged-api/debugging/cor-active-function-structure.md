---
title: "COR_ACTIVE_FUNCTION – struktura"
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
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7bb587f485427d9fd88e2f834d844ece18d336ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="e2a5e-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="e2a5e-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="e2a5e-103">Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="e2a5e-104">Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a5e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2a5e-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="e2a5e-106">Členové</span><span class="sxs-lookup"><span data-stu-id="e2a5e-106">Members</span></span>  
  
|<span data-ttu-id="e2a5e-107">Člen</span><span class="sxs-lookup"><span data-stu-id="e2a5e-107">Member</span></span>|<span data-ttu-id="e2a5e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e2a5e-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="e2a5e-109">Ukazatel na vlastníkem domény aplikace `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="e2a5e-110">Ukazatel na modulu vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="e2a5e-111">Ukazatel na funkci vlastník `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="e2a5e-112">Posun Microsoft (MSIL intermediate language) rámečku.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="e2a5e-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e2a5e-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2a5e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2a5e-114">Requirements</span></span>  
 <span data-ttu-id="e2a5e-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a5e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a5e-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e2a5e-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e2a5e-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2a5e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2a5e-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a5e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a5e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2a5e-119">See Also</span></span>  
 [<span data-ttu-id="e2a5e-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2a5e-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="e2a5e-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e2a5e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
