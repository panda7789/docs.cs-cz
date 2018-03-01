---
title: "CorDebugExceptionFlags – výčet"
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
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1b25211c8e7f03cc09e8729abc44af39f0c84259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="77735-102">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="77735-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="77735-103">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="77735-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77735-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77735-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="77735-105">Členové</span><span class="sxs-lookup"><span data-stu-id="77735-105">Members</span></span>  
  
|<span data-ttu-id="77735-106">Člen</span><span class="sxs-lookup"><span data-stu-id="77735-106">Member</span></span>|<span data-ttu-id="77735-107">Popis</span><span class="sxs-lookup"><span data-stu-id="77735-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="77735-108">Neexistuje žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="77735-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="77735-109">Výjimkou je interceptable.</span><span class="sxs-lookup"><span data-stu-id="77735-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="77735-110">Načasování výjimky stále může být tak, aby ladicí program nemůže zachytit ho.</span><span class="sxs-lookup"><span data-stu-id="77735-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="77735-111">Například pokud není žádný spravovaný kód pod aktuální zpětného volání nebo události výjimky je výsledkem přílohy za běhu (JIT), nelze výjimka zachycena.</span><span class="sxs-lookup"><span data-stu-id="77735-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77735-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77735-112">Remarks</span></span>  
 <span data-ttu-id="77735-113">Nové hodnoty mohou být přidány do tento výčet v novějších verzích, měli byste kód, který používá `CorDebugExceptionFlags` neočekávané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="77735-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77735-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77735-114">Requirements</span></span>  
 <span data-ttu-id="77735-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77735-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77735-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77735-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77735-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77735-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77735-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77735-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77735-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="77735-119">See Also</span></span>  
 [<span data-ttu-id="77735-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="77735-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
