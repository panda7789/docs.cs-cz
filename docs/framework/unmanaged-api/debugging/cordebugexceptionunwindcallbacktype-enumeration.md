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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef3f1d5e78efe37070bb2bdd6d2834178947af7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740084"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="243ba-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="243ba-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="243ba-103">Určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.</span><span class="sxs-lookup"><span data-stu-id="243ba-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="243ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="243ba-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="243ba-105">Členové</span><span class="sxs-lookup"><span data-stu-id="243ba-105">Members</span></span>  
  
|<span data-ttu-id="243ba-106">Člen</span><span class="sxs-lookup"><span data-stu-id="243ba-106">Member</span></span>|<span data-ttu-id="243ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="243ba-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="243ba-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="243ba-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="243ba-109">Byla zachycena výjimka.</span><span class="sxs-lookup"><span data-stu-id="243ba-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="243ba-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="243ba-110">Requirements</span></span>  
 <span data-ttu-id="243ba-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="243ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="243ba-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="243ba-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="243ba-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="243ba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="243ba-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="243ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="243ba-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="243ba-115">See also</span></span>

- [<span data-ttu-id="243ba-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="243ba-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
