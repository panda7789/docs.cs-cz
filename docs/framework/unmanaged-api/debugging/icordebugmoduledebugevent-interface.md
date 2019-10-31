---
title: ICorDebugModuleDebugEvent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: cca181c6af6db9f35ff7913e045a30e37e07a5e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110239"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="fd4d5-102">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd4d5-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="fd4d5-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="fd4d5-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fd4d5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fd4d5-104">Methods</span></span>  
  
|<span data-ttu-id="fd4d5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fd4d5-105">Method</span></span>|<span data-ttu-id="fd4d5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fd4d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fd4d5-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fd4d5-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="fd4d5-108">Získá sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="fd4d5-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd4d5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd4d5-109">Remarks</span></span>  
 <span data-ttu-id="fd4d5-110">Typy událostí [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd4d5-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd4d5-111">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd4d5-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="fd4d5-112">Pokus o volání `QueryInterface` pro načtení ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fd4d5-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd4d5-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd4d5-113">Requirements</span></span>  
 <span data-ttu-id="fd4d5-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd4d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd4d5-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd4d5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd4d5-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fd4d5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd4d5-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd4d5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4d5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd4d5-118">See also</span></span>

- [<span data-ttu-id="fd4d5-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fd4d5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fd4d5-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="fd4d5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
