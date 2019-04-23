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
ms.openlocfilehash: 9e5479fad3f19c219a0ca1d5d01934ce92a7162e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127160"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="6cacb-102">Výčet CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="6cacb-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="6cacb-103">Určuje typ události, jejichž informace je dekódováno pomocí [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6cacb-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cacb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cacb-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6cacb-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6cacb-105">Members</span></span>  
  
|<span data-ttu-id="6cacb-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6cacb-106">Member</span></span>|<span data-ttu-id="6cacb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6cacb-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="6cacb-108">Události načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="6cacb-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="6cacb-109">Vytvoření události uvolnění modulu.</span><span class="sxs-lookup"><span data-stu-id="6cacb-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="6cacb-110">První odpovídající výjimce.</span><span class="sxs-lookup"><span data-stu-id="6cacb-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="6cacb-111">Výjimka první příležitosti uživatele.</span><span class="sxs-lookup"><span data-stu-id="6cacb-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="6cacb-112">Výjimka pro kterou `catch` obslužná rutina existuje.</span><span class="sxs-lookup"><span data-stu-id="6cacb-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="6cacb-113">Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="6cacb-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cacb-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cacb-114">Remarks</span></span>  
 <span data-ttu-id="6cacb-115">Členem `CorDebugDebugEventKind` výčtu je vrácený voláním [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6cacb-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cacb-116">Tento výčet je určena pro použití v .NET Native ladění pouze scénáře.</span><span class="sxs-lookup"><span data-stu-id="6cacb-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cacb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cacb-117">Requirements</span></span>  
 <span data-ttu-id="6cacb-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cacb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cacb-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cacb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cacb-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cacb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cacb-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cacb-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cacb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cacb-122">See also</span></span>

- [<span data-ttu-id="6cacb-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="6cacb-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
