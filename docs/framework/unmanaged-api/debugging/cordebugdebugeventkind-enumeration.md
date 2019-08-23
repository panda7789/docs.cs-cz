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
ms.openlocfilehash: d2e01a5cf2b2aa25e91ebf0f8e3927858b12bea3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967567"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="7b159-102">Výčet CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="7b159-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="7b159-103">Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7b159-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b159-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b159-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7b159-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7b159-105">Members</span></span>  
  
|<span data-ttu-id="7b159-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7b159-106">Member</span></span>|<span data-ttu-id="7b159-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b159-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="7b159-108">Událost načtení modulu.</span><span class="sxs-lookup"><span data-stu-id="7b159-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="7b159-109">Událost uvolnění modulu</span><span class="sxs-lookup"><span data-stu-id="7b159-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="7b159-110">První pravděpodobnost výjimky.</span><span class="sxs-lookup"><span data-stu-id="7b159-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="7b159-111">Uživatelská výjimka první pravděpodobnosti.</span><span class="sxs-lookup"><span data-stu-id="7b159-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="7b159-112">Výjimka, pro kterou `catch` existuje obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="7b159-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="7b159-113">Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="7b159-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b159-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b159-114">Remarks</span></span>  
 <span data-ttu-id="7b159-115">Člen `CorDebugDebugEventKind` výčtu je vrácen voláním metody [ICorDebugDebugEvent:: GetEventKind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7b159-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b159-116">Tento výčet je určený pro použití pouze v .NET Nativech scénářích ladění.</span><span class="sxs-lookup"><span data-stu-id="7b159-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b159-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b159-117">Requirements</span></span>  
 <span data-ttu-id="7b159-118">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b159-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b159-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b159-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b159-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b159-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b159-121">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b159-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b159-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b159-122">See also</span></span>

- [<span data-ttu-id="7b159-123">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="7b159-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
