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
ms.openlocfilehash: e714c41812c8aaccd713115712df05744cc015e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789389"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="2202e-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="2202e-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="2202e-103">Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2202e-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2202e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2202e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="2202e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2202e-105">Members</span></span>  
  
|<span data-ttu-id="2202e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2202e-106">Member</span></span>|<span data-ttu-id="2202e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2202e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="2202e-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="2202e-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="2202e-109">Výjimka byla zachycena.</span><span class="sxs-lookup"><span data-stu-id="2202e-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2202e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2202e-110">Requirements</span></span>  
 <span data-ttu-id="2202e-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2202e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2202e-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2202e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2202e-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2202e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2202e-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2202e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2202e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2202e-115">See also</span></span>

- [<span data-ttu-id="2202e-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="2202e-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
