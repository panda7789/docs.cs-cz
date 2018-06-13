---
title: COR_ACTIVE_FUNCTION – struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86ab3d3a0f460f1ecdf86147b14df205aaf49635
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404194"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="34a04-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="34a04-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="34a04-103">Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="34a04-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="34a04-104">Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="34a04-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34a04-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34a04-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="34a04-106">Členové</span><span class="sxs-lookup"><span data-stu-id="34a04-106">Members</span></span>  
  
|<span data-ttu-id="34a04-107">Člen</span><span class="sxs-lookup"><span data-stu-id="34a04-107">Member</span></span>|<span data-ttu-id="34a04-108">Popis</span><span class="sxs-lookup"><span data-stu-id="34a04-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="34a04-109">Ukazatel na vlastníkem domény aplikace `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="34a04-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="34a04-110">Ukazatel na modulu vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="34a04-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="34a04-111">Ukazatel na funkci vlastník `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="34a04-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="34a04-112">Posun Microsoft (MSIL intermediate language) rámečku.</span><span class="sxs-lookup"><span data-stu-id="34a04-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="34a04-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="34a04-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34a04-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34a04-114">Requirements</span></span>  
 <span data-ttu-id="34a04-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34a04-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34a04-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="34a04-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="34a04-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34a04-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34a04-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34a04-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a04-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="34a04-119">See Also</span></span>  
 [<span data-ttu-id="34a04-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="34a04-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="34a04-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="34a04-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
