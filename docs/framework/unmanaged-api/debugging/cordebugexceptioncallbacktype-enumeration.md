---
title: CorDebugExceptionCallbackType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e9a3b0320ac0be785f0823afef1819ab8a35eb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585546"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="c2cea-102">CorDebugExceptionCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="c2cea-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="c2cea-103">Určuje typ zpětné volání, které se provádí ze [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.</span><span class="sxs-lookup"><span data-stu-id="c2cea-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2cea-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="c2cea-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c2cea-105">Members</span></span>  
  
|<span data-ttu-id="c2cea-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c2cea-106">Member</span></span>|<span data-ttu-id="c2cea-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c2cea-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="c2cea-108">Došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="c2cea-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="c2cea-109">Proces windup výjimka zadaný uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="c2cea-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="c2cea-110">Proces windup výjimka nalezen `catch` blokovat v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="c2cea-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="c2cea-111">Tato výjimka není ošetřena.</span><span class="sxs-lookup"><span data-stu-id="c2cea-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2cea-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2cea-112">Requirements</span></span>  
 <span data-ttu-id="c2cea-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2cea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2cea-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2cea-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2cea-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2cea-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2cea-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2cea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cea-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2cea-117">See also</span></span>
- [<span data-ttu-id="c2cea-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="c2cea-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
