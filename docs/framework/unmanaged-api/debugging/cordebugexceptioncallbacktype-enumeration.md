---
title: "CorDebugExceptionCallbackType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionCallbackType
helpviewer_keywords: CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4efc969395e30dcc237d2ad99c9bc67ee30f4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="3b2cc-102">CorDebugExceptionCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="3b2cc-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="3b2cc-103">Určuje typ zpětné volání, které se provádí z [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.</span><span class="sxs-lookup"><span data-stu-id="3b2cc-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b2cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b2cc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="3b2cc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3b2cc-105">Members</span></span>  
  
|<span data-ttu-id="3b2cc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3b2cc-106">Member</span></span>|<span data-ttu-id="3b2cc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3b2cc-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="3b2cc-108">Došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="3b2cc-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="3b2cc-109">Proces windup výjimka zadali kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="3b2cc-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="3b2cc-110">Proces windup výjimka najít `catch` blokovat v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="3b2cc-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="3b2cc-111">Výjimka nebyla zpracována.</span><span class="sxs-lookup"><span data-stu-id="3b2cc-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b2cc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b2cc-112">Requirements</span></span>  
 <span data-ttu-id="3b2cc-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b2cc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b2cc-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b2cc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b2cc-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b2cc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b2cc-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b2cc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b2cc-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b2cc-117">See Also</span></span>  
 [<span data-ttu-id="3b2cc-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="3b2cc-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
