---
title: Výčet CorDebugDebugEventKind
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be8d860f508644e68bf69892a63e145e7ffd5b90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740245"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="2a705-102">Výčet CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="2a705-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="2a705-103">Určuje typ události, jejichž informace je dekódováno pomocí [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a705-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a705-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a705-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="2a705-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2a705-105">Members</span></span>  
  
|<span data-ttu-id="2a705-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2a705-106">Member</span></span>|<span data-ttu-id="2a705-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2a705-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="2a705-108">Události načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="2a705-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="2a705-109">Vytvoření události uvolnění modulu.</span><span class="sxs-lookup"><span data-stu-id="2a705-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="2a705-110">První odpovídající výjimce.</span><span class="sxs-lookup"><span data-stu-id="2a705-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="2a705-111">Výjimka první příležitosti uživatele.</span><span class="sxs-lookup"><span data-stu-id="2a705-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="2a705-112">Výjimka pro kterou `catch` obslužná rutina existuje.</span><span class="sxs-lookup"><span data-stu-id="2a705-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="2a705-113">Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="2a705-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a705-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a705-114">Remarks</span></span>  
 <span data-ttu-id="2a705-115">Členem `CorDebugDebugEventKind` výčtu je vrácený voláním [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a705-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a705-116">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="2a705-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a705-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a705-117">Requirements</span></span>  
 <span data-ttu-id="2a705-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a705-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a705-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a705-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a705-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a705-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a705-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a705-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a705-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a705-122">See also</span></span>

- [<span data-ttu-id="2a705-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="2a705-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
