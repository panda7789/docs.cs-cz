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
ms.openlocfilehash: 408e72eeaa1dac83c45488d186425f30c6043280
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786370"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="ebeef-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="ebeef-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="ebeef-103">Určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.</span><span class="sxs-lookup"><span data-stu-id="ebeef-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebeef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebeef-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="ebeef-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ebeef-105">Members</span></span>  
  
|<span data-ttu-id="ebeef-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ebeef-106">Member</span></span>|<span data-ttu-id="ebeef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ebeef-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="ebeef-108">Začátek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="ebeef-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="ebeef-109">Byla zachycena výjimka.</span><span class="sxs-lookup"><span data-stu-id="ebeef-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebeef-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ebeef-110">Requirements</span></span>  
 <span data-ttu-id="ebeef-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebeef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebeef-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebeef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebeef-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebeef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebeef-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebeef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebeef-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebeef-115">See also</span></span>

- [<span data-ttu-id="ebeef-116">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ebeef-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
