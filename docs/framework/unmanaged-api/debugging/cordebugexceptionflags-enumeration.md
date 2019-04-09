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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078704"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="f596b-102">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f596b-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="f596b-103">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f596b-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f596b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f596b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f596b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f596b-105">Members</span></span>  
  
|<span data-ttu-id="f596b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f596b-106">Member</span></span>|<span data-ttu-id="f596b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f596b-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="f596b-108">Není žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="f596b-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="f596b-109">Výjimkou je interceptable.</span><span class="sxs-lookup"><span data-stu-id="f596b-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="f596b-110">Načasování výjimky může být stále tak, aby ladicí program nemůže zachytit.</span><span class="sxs-lookup"><span data-stu-id="f596b-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="f596b-111">Například pokud neexistuje žádný spravovaný kód pod aktuální zpětného volání nebo událost výjimky je výsledkem přílohy k just-in-time (JIT), nelze zachytit výjimku.</span><span class="sxs-lookup"><span data-stu-id="f596b-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f596b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f596b-112">Remarks</span></span>  
 <span data-ttu-id="f596b-113">Nové hodnoty lze přidat na tento výčet v novějších verzích, připravte si kód, který používá `CorDebugExceptionFlags` pro neočekávané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f596b-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f596b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f596b-114">Requirements</span></span>  
 <span data-ttu-id="f596b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f596b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f596b-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f596b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f596b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f596b-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f596b-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f596b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f596b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f596b-119">See also</span></span>

- [<span data-ttu-id="f596b-120">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="f596b-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
