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
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121768"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="c1f99-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="c1f99-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="c1f99-103">Obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.</span><span class="sxs-lookup"><span data-stu-id="c1f99-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="c1f99-104">Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c1f99-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f99-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1f99-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="c1f99-106">Členové</span><span class="sxs-lookup"><span data-stu-id="c1f99-106">Members</span></span>  
  
|<span data-ttu-id="c1f99-107">Člen</span><span class="sxs-lookup"><span data-stu-id="c1f99-107">Member</span></span>|<span data-ttu-id="c1f99-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c1f99-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="c1f99-109">Ukazatel na vlastník domény aplikace `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="c1f99-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="c1f99-110">Ukazatel na vlastníka modulu `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="c1f99-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="c1f99-111">Ukazatel na funkci vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="c1f99-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="c1f99-112">Posun Microsoft intermediate language (MSIL) rámce.</span><span class="sxs-lookup"><span data-stu-id="c1f99-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="c1f99-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c1f99-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1f99-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1f99-114">Requirements</span></span>  
 <span data-ttu-id="c1f99-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1f99-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f99-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c1f99-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c1f99-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1f99-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c1f99-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c1f99-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1f99-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1f99-119">See also</span></span>

- [<span data-ttu-id="c1f99-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="c1f99-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="c1f99-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="c1f99-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
