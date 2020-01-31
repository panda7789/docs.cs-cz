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
ms.openlocfilehash: 977b1608539a302c6a27a1b54cfb2ad687025fe6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789410"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="45948-102">CorDebugExceptionCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="45948-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="45948-103">Určuje typ zpětného volání, které je provedeno z události [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45948-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45948-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45948-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="45948-105">Členové</span><span class="sxs-lookup"><span data-stu-id="45948-105">Members</span></span>  
  
|<span data-ttu-id="45948-106">Člen</span><span class="sxs-lookup"><span data-stu-id="45948-106">Member</span></span>|<span data-ttu-id="45948-107">Popis</span><span class="sxs-lookup"><span data-stu-id="45948-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="45948-108">Vyvolala se výjimka.</span><span class="sxs-lookup"><span data-stu-id="45948-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="45948-109">Výjimka windup zadává uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="45948-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="45948-110">Proces windup výjimky nalezl v uživatelském kódu blok `catch`.</span><span class="sxs-lookup"><span data-stu-id="45948-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="45948-111">Výjimka nebyla zpracována.</span><span class="sxs-lookup"><span data-stu-id="45948-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45948-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45948-112">Requirements</span></span>  
 <span data-ttu-id="45948-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45948-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45948-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45948-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45948-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="45948-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45948-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45948-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45948-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45948-117">See also</span></span>

- [<span data-ttu-id="45948-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="45948-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
