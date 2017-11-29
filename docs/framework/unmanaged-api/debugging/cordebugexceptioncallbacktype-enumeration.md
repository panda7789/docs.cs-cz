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
ms.openlocfilehash: dfffea1044eb2c1e771fe86e5e9b431eb0ab9696
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="dd0d4-102">CorDebugExceptionCallbackType – výčet</span><span class="sxs-lookup"><span data-stu-id="dd0d4-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="dd0d4-103">Určuje typ zpětné volání, které se provádí z [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.</span><span class="sxs-lookup"><span data-stu-id="dd0d4-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd0d4-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="dd0d4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dd0d4-105">Members</span></span>  
  
|<span data-ttu-id="dd0d4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dd0d4-106">Member</span></span>|<span data-ttu-id="dd0d4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dd0d4-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="dd0d4-108">Došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="dd0d4-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="dd0d4-109">Proces windup výjimka zadali kód uživatele.</span><span class="sxs-lookup"><span data-stu-id="dd0d4-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="dd0d4-110">Proces windup výjimka najít `catch` blokovat v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="dd0d4-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="dd0d4-111">Výjimka nebyla zpracována.</span><span class="sxs-lookup"><span data-stu-id="dd0d4-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd0d4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd0d4-112">Requirements</span></span>  
 <span data-ttu-id="dd0d4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd0d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd0d4-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd0d4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd0d4-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd0d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd0d4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd0d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0d4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd0d4-117">See Also</span></span>  
 [<span data-ttu-id="dd0d4-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="dd0d4-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
