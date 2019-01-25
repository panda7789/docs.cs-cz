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
ms.openlocfilehash: 31b302977950b3daeab6ac2be117c7f8db51eb2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654760"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="7eb6a-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="7eb6a-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="7eb6a-103">Určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb6a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="7eb6a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7eb6a-105">Members</span></span>  
  
|<span data-ttu-id="7eb6a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7eb6a-106">Member</span></span>|<span data-ttu-id="7eb6a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7eb6a-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="7eb6a-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="7eb6a-109">Byla zachycena výjimka.</span><span class="sxs-lookup"><span data-stu-id="7eb6a-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7eb6a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7eb6a-110">Requirements</span></span>  
 <span data-ttu-id="7eb6a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb6a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eb6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eb6a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eb6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eb6a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb6a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7eb6a-115">See also</span></span>
- [<span data-ttu-id="7eb6a-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7eb6a-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
