---
title: "COR_ACTIVE_FUNCTION – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85096b607fa2fec9875e497cc1f50167fc482fbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="819f6-102">COR_ACTIVE_FUNCTION – struktura</span><span class="sxs-lookup"><span data-stu-id="819f6-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="819f6-103">Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="819f6-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="819f6-104">Tato struktura je používán [icordebugthread2::getactivefunctions –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="819f6-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="819f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="819f6-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="819f6-106">Členové</span><span class="sxs-lookup"><span data-stu-id="819f6-106">Members</span></span>  
  
|<span data-ttu-id="819f6-107">Člen</span><span class="sxs-lookup"><span data-stu-id="819f6-107">Member</span></span>|<span data-ttu-id="819f6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="819f6-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="819f6-109">Ukazatel na vlastníkem domény aplikace `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="819f6-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="819f6-110">Ukazatel na modulu vlastníka `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="819f6-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="819f6-111">Ukazatel na funkci vlastník `ilOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="819f6-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="819f6-112">Posun Microsoft (MSIL intermediate language) rámečku.</span><span class="sxs-lookup"><span data-stu-id="819f6-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="819f6-113">Vyhrazeno pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="819f6-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="819f6-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="819f6-114">Requirements</span></span>  
 <span data-ttu-id="819f6-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="819f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="819f6-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="819f6-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="819f6-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="819f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="819f6-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="819f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="819f6-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="819f6-119">See Also</span></span>  
 [<span data-ttu-id="819f6-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="819f6-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="819f6-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="819f6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
