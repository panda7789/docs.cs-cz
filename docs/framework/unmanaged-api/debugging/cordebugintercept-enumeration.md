---
title: CorDebugIntercept – výčet
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
ms.openlocfilehash: 18a5e337b6026a20a95b1c29f3d7bda5187efc66
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795856"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="b01c0-102">CorDebugIntercept – výčet</span><span class="sxs-lookup"><span data-stu-id="b01c0-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="b01c0-103">Určuje typy kódu, které mohou být zachyceny (to je od-steped do).</span><span class="sxs-lookup"><span data-stu-id="b01c0-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b01c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b01c0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="b01c0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b01c0-105">Members</span></span>  
  
|<span data-ttu-id="b01c0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b01c0-106">Member</span></span>|<span data-ttu-id="b01c0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b01c0-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="b01c0-108">Nelze zachytit žádný kód.</span><span class="sxs-lookup"><span data-stu-id="b01c0-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="b01c0-109">Může být zachycen konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b01c0-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="b01c0-110">Je možné zachytit filtr výjimky.</span><span class="sxs-lookup"><span data-stu-id="b01c0-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="b01c0-111">Kód, který vynutil zabezpečení, lze zachytit.</span><span class="sxs-lookup"><span data-stu-id="b01c0-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="b01c0-112">Můžete zachytit zásady kontextu.</span><span class="sxs-lookup"><span data-stu-id="b01c0-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="b01c0-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="b01c0-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="b01c0-114">Veškerý kód může být zachycen.</span><span class="sxs-lookup"><span data-stu-id="b01c0-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b01c0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b01c0-115">Remarks</span></span>  
 <span data-ttu-id="b01c0-116">Použijte metodu [ICorDebugStepper:: SetInterceptMask –](icordebugstepper-setinterceptmask-method.md) pro vytvoření typů kódu, který lze zachytit.</span><span class="sxs-lookup"><span data-stu-id="b01c0-116">Use the [ICorDebugStepper::SetInterceptMask](icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b01c0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b01c0-117">Requirements</span></span>  
 <span data-ttu-id="b01c0-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b01c0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b01c0-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b01c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b01c0-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b01c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b01c0-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b01c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b01c0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b01c0-122">See also</span></span>

- [<span data-ttu-id="b01c0-123">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b01c0-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
