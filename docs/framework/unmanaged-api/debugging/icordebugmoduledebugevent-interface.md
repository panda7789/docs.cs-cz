---
title: ICorDebugModuleDebugEvent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 706f392652c5cb868e09d4ee9fcb69c6d3d92d2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965089"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="4afa3-102">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4afa3-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="4afa3-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="4afa3-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4afa3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4afa3-104">Methods</span></span>  
  
|<span data-ttu-id="4afa3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4afa3-105">Method</span></span>|<span data-ttu-id="4afa3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4afa3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4afa3-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="4afa3-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="4afa3-108">Získá sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="4afa3-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4afa3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4afa3-109">Remarks</span></span>  
 <span data-ttu-id="4afa3-110">Typy událostí [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4afa3-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4afa3-111">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4afa3-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4afa3-112">Pokus o volání metody `QueryInterface` načtení `E_NOINTERFACE` ukazatele rozhraní pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4afa3-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4afa3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4afa3-113">Requirements</span></span>  
 <span data-ttu-id="4afa3-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4afa3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4afa3-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4afa3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4afa3-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4afa3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4afa3-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4afa3-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afa3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4afa3-118">See also</span></span>

- [<span data-ttu-id="4afa3-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4afa3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4afa3-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="4afa3-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
