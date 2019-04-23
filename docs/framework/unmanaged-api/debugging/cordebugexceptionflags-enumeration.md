---
title: CorDebugExceptionFlags – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7b9b25673685dde8b75702c80f525515917ae1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078704"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="336c1-102">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="336c1-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="336c1-103">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="336c1-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336c1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="336c1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="336c1-105">Members</span></span>  
  
|<span data-ttu-id="336c1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="336c1-106">Member</span></span>|<span data-ttu-id="336c1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="336c1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="336c1-108">Není žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="336c1-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="336c1-109">Výjimkou je interceptable.</span><span class="sxs-lookup"><span data-stu-id="336c1-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="336c1-110">Načasování výjimky může být stále tak, aby ladicí program nemůže zachytit.</span><span class="sxs-lookup"><span data-stu-id="336c1-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="336c1-111">Například pokud neexistuje žádný spravovaný kód pod aktuální zpětného volání nebo událost výjimky je výsledkem přílohy k just-in-time (JIT), nelze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="336c1-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336c1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="336c1-112">Remarks</span></span>  
 <span data-ttu-id="336c1-113">Nové hodnoty lze přidat na tento výčet v novějších verzích, připravte si kód, který používá `CorDebugExceptionFlags` pro neočekávané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="336c1-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336c1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="336c1-114">Requirements</span></span>  
 <span data-ttu-id="336c1-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="336c1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336c1-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="336c1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="336c1-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="336c1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="336c1-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336c1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336c1-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="336c1-119">See also</span></span>

- [<span data-ttu-id="336c1-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="336c1-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
