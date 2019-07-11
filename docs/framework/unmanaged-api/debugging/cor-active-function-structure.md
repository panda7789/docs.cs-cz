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
ms.openlocfilehash: 6875ce0e7ae4cefa9b0c8abaded0dd4535bdf838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740822"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="6f9bc-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="6f9bc-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="6f9bc-103">Obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="6f9bc-104">Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f9bc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f9bc-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="6f9bc-106">Členové</span><span class="sxs-lookup"><span data-stu-id="6f9bc-106">Members</span></span>  
  
|<span data-ttu-id="6f9bc-107">Člen</span><span class="sxs-lookup"><span data-stu-id="6f9bc-107">Member</span></span>|<span data-ttu-id="6f9bc-108">Popis</span><span class="sxs-lookup"><span data-stu-id="6f9bc-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="6f9bc-109">Ukazatel na vlastník domény aplikace `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="6f9bc-110">Ukazatel na vlastníka modulu `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="6f9bc-111">Ukazatel na funkci vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="6f9bc-112">Posun Microsoft intermediate language (MSIL) rámce.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="6f9bc-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6f9bc-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f9bc-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f9bc-114">Requirements</span></span>  
 <span data-ttu-id="6f9bc-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f9bc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f9bc-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="6f9bc-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="6f9bc-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f9bc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f9bc-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f9bc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9bc-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f9bc-119">See also</span></span>

- [<span data-ttu-id="6f9bc-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="6f9bc-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="6f9bc-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="6f9bc-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
