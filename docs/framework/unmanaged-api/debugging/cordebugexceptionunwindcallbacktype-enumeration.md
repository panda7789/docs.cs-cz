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
ms.openlocfilehash: 4d2be9960f8935b754791a8badd4ea98b5d54912
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795908"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="c4f77-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="c4f77-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="c4f77-103">Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="c4f77-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4f77-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="c4f77-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c4f77-105">Members</span></span>  
  
|<span data-ttu-id="c4f77-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c4f77-106">Member</span></span>|<span data-ttu-id="c4f77-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4f77-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="c4f77-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="c4f77-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="c4f77-109">Výjimka byla zachycena.</span><span class="sxs-lookup"><span data-stu-id="c4f77-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4f77-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4f77-110">Requirements</span></span>  
 <span data-ttu-id="c4f77-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f77-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4f77-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4f77-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4f77-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c4f77-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4f77-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f77-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f77-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4f77-115">See also</span></span>

- [<span data-ttu-id="c4f77-116">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="c4f77-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
