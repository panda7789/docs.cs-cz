---
title: CorDebugExceptionUnwindCallbackType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 5004cd293b64436c41caef1c7393d2229d1a6ccf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098484"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="65c75-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="65c75-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="65c75-103">Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="65c75-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c75-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="65c75-105">Členové</span><span class="sxs-lookup"><span data-stu-id="65c75-105">Members</span></span>  
  
|<span data-ttu-id="65c75-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65c75-106">Member</span></span>|<span data-ttu-id="65c75-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65c75-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="65c75-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="65c75-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="65c75-109">Výjimka byla zachycena.</span><span class="sxs-lookup"><span data-stu-id="65c75-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65c75-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65c75-110">Requirements</span></span>  
 <span data-ttu-id="65c75-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c75-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c75-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65c75-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65c75-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65c75-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65c75-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c75-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c75-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65c75-115">See also</span></span>

- [<span data-ttu-id="65c75-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="65c75-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
