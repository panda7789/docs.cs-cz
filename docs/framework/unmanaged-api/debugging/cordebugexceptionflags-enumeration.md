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
ms.openlocfilehash: 198de0aed4e229d7ed8bb1679afc3a0102bd5368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098467"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="a4c56-102">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="a4c56-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="a4c56-103">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="a4c56-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4c56-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a4c56-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a4c56-105">Members</span></span>  
  
|<span data-ttu-id="a4c56-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a4c56-106">Member</span></span>|<span data-ttu-id="a4c56-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a4c56-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="a4c56-108">Neexistuje žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="a4c56-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="a4c56-109">Výjimka je zachytila.</span><span class="sxs-lookup"><span data-stu-id="a4c56-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="a4c56-110">Načasování výjimky může být stále tak, aby ji ladicí program nemohl zachytit.</span><span class="sxs-lookup"><span data-stu-id="a4c56-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="a4c56-111">Například pokud neexistuje žádný spravovaný kód pod aktuálním zpětným voláním nebo událost výjimky, která je výsledkem přílohy just-in-time (JIT), nelze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="a4c56-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4c56-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4c56-112">Remarks</span></span>  
 <span data-ttu-id="a4c56-113">Do tohoto výčtu lze přidat nové hodnoty v pozdějších verzích, proto byste měli připravit kód, který používá `CorDebugExceptionFlags` pro neočekávané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a4c56-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c56-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4c56-114">Requirements</span></span>  
 <span data-ttu-id="a4c56-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c56-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c56-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4c56-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4c56-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4c56-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4c56-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c56-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4c56-119">See also</span></span>

- [<span data-ttu-id="a4c56-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="a4c56-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
