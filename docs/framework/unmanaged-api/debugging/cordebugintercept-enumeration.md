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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 148bc423a9497962ebfbc73faefcc799c6db6499
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739897"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="ee546-102">CorDebugIntercept – výčet</span><span class="sxs-lookup"><span data-stu-id="ee546-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="ee546-103">Určuje typy kód, který může být zachycen (které je, vkročili).</span><span class="sxs-lookup"><span data-stu-id="ee546-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee546-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee546-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ee546-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ee546-105">Members</span></span>  
  
|<span data-ttu-id="ee546-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ee546-106">Member</span></span>|<span data-ttu-id="ee546-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ee546-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="ee546-108">Žádný kód může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="ee546-109">Konstruktor může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="ee546-110">Filtru výjimky může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="ee546-111">Kód, který vynucuje zabezpečení může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="ee546-112">Kontext zásad může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="ee546-113">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="ee546-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="ee546-114">Veškerý kód může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee546-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee546-115">Remarks</span></span>  
 <span data-ttu-id="ee546-116">Použití [icordebugstepper::setinterceptmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metodu pro vytvoření typy kódu, který může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="ee546-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee546-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee546-117">Requirements</span></span>  
 <span data-ttu-id="ee546-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee546-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee546-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee546-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee546-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee546-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee546-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee546-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee546-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee546-122">See also</span></span>

- [<span data-ttu-id="ee546-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ee546-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
