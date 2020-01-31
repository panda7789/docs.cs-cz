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
ms.openlocfilehash: 6ef81e224f3573021ee96ac313ec4923928dedad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789401"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="29c7e-102">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="29c7e-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="29c7e-103">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="29c7e-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c7e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="29c7e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="29c7e-105">Members</span></span>  
  
|<span data-ttu-id="29c7e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="29c7e-106">Member</span></span>|<span data-ttu-id="29c7e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="29c7e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="29c7e-108">Neexistuje žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="29c7e-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="29c7e-109">Výjimka je zachytila.</span><span class="sxs-lookup"><span data-stu-id="29c7e-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="29c7e-110">Načasování výjimky může být stále tak, aby ji ladicí program nemohl zachytit.</span><span class="sxs-lookup"><span data-stu-id="29c7e-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="29c7e-111">Například pokud neexistuje žádný spravovaný kód pod aktuálním zpětným voláním nebo událost výjimky, která je výsledkem přílohy just-in-time (JIT), nelze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="29c7e-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29c7e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29c7e-112">Remarks</span></span>  
 <span data-ttu-id="29c7e-113">Do tohoto výčtu lze přidat nové hodnoty v pozdějších verzích, proto byste měli připravit kód, který používá `CorDebugExceptionFlags` pro neočekávané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29c7e-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c7e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29c7e-114">Requirements</span></span>  
 <span data-ttu-id="29c7e-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c7e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c7e-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29c7e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29c7e-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29c7e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c7e-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c7e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c7e-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29c7e-119">See also</span></span>

- [<span data-ttu-id="29c7e-120">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="29c7e-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
