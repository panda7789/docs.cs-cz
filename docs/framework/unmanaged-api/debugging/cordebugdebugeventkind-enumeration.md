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
ms.openlocfilehash: b7db7c9e17d87b91e09d5d010d40431cba5385df
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795986"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="8ec41-102">Výčet CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="8ec41-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="8ec41-103">Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ec41-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ec41-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8ec41-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8ec41-105">Members</span></span>  
  
|<span data-ttu-id="8ec41-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8ec41-106">Member</span></span>|<span data-ttu-id="8ec41-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8ec41-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="8ec41-108">Událost načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="8ec41-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="8ec41-109">Událost uvolnění modulu</span><span class="sxs-lookup"><span data-stu-id="8ec41-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="8ec41-110">První pravděpodobnost výjimky.</span><span class="sxs-lookup"><span data-stu-id="8ec41-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="8ec41-111">Uživatelská výjimka první pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="8ec41-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="8ec41-112">Výjimka, pro kterou existuje `catch` obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="8ec41-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="8ec41-113">Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="8ec41-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ec41-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ec41-114">Remarks</span></span>  
 <span data-ttu-id="8ec41-115">Člen `CorDebugDebugEventKind` výčtu je vrácen voláním metody [ICorDebugDebugEvent:: GetEventKind –](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8ec41-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ec41-116">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="8ec41-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ec41-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ec41-117">Requirements</span></span>  
 <span data-ttu-id="8ec41-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ec41-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ec41-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ec41-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ec41-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8ec41-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ec41-121">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec41-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec41-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ec41-122">See also</span></span>

- [<span data-ttu-id="8ec41-123">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="8ec41-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
