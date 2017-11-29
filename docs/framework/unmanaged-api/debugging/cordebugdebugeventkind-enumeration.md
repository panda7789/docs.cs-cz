---
title: "Výčet CorDebugDebugEventKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDebugEventKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5aeb6085671e645e12713944d6456b9581a3886f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="36ab0-102">Výčet CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="36ab0-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="36ab0-103">Určuje typ události, jejichž informace dekóduje ji [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="36ab0-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ab0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36ab0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="36ab0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="36ab0-105">Members</span></span>  
  
|<span data-ttu-id="36ab0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="36ab0-106">Member</span></span>|<span data-ttu-id="36ab0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="36ab0-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="36ab0-108">O modulu zatížení událost.</span><span class="sxs-lookup"><span data-stu-id="36ab0-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="36ab0-109">O událost uvolnění modulu.</span><span class="sxs-lookup"><span data-stu-id="36ab0-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="36ab0-110">První odpovídající výjimce.</span><span class="sxs-lookup"><span data-stu-id="36ab0-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="36ab0-111">Uživatel první odpovídající výjimce.</span><span class="sxs-lookup"><span data-stu-id="36ab0-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="36ab0-112">Výjimku, pro který `catch` obslužná rutina existuje.</span><span class="sxs-lookup"><span data-stu-id="36ab0-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="36ab0-113">K neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="36ab0-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36ab0-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36ab0-114">Remarks</span></span>  
 <span data-ttu-id="36ab0-115">Členem `CorDebugDebugEventKind` výčtu vrátí volání [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="36ab0-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="36ab0-116">Tento výčet je určena pro použití v rozhraní .NET nativní ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="36ab0-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ab0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36ab0-117">Requirements</span></span>  
 <span data-ttu-id="36ab0-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ab0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36ab0-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36ab0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36ab0-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36ab0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36ab0-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36ab0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ab0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="36ab0-122">See Also</span></span>  
 [<span data-ttu-id="36ab0-123">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="36ab0-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
