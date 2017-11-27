---
title: "CorDebugExceptionUnwindCallbackType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionUnwindCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionUnwindCallbackType
helpviewer_keywords: CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8528b2839c4972dd44f03db5f331acb672cfeb71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="001de-102">CorDebugExceptionUnwindCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="001de-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="001de-103">Označuje událost, která se během fáze unwind signalizace podle zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="001de-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="001de-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="001de-105">Členové</span><span class="sxs-lookup"><span data-stu-id="001de-105">Members</span></span>  
  
|<span data-ttu-id="001de-106">Člen</span><span class="sxs-lookup"><span data-stu-id="001de-106">Member</span></span>|<span data-ttu-id="001de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="001de-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="001de-108">Začátku procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="001de-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="001de-109">Byla výjimka zachycena.</span><span class="sxs-lookup"><span data-stu-id="001de-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="001de-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="001de-110">Requirements</span></span>  
 <span data-ttu-id="001de-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="001de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="001de-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="001de-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="001de-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="001de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="001de-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="001de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001de-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="001de-115">See Also</span></span>  
 [<span data-ttu-id="001de-116">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="001de-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
