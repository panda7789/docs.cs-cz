---
title: Icordebugmoduledebugevent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 399f27db0a2d18e3bcd90b87f4470a77cb50595d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646853"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="57879-102">Icordebugmoduledebugevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57879-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="57879-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="57879-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57879-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57879-104">Methods</span></span>  
  
|<span data-ttu-id="57879-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57879-105">Method</span></span>|<span data-ttu-id="57879-106">Popis</span><span class="sxs-lookup"><span data-stu-id="57879-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57879-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="57879-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="57879-108">Získá sloučené modul, který byl právě nenačetl nebo je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="57879-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57879-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57879-109">Remarks</span></span>  
 <span data-ttu-id="57879-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) toto rozhraní implementují typy událostí.</span><span class="sxs-lookup"><span data-stu-id="57879-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57879-111">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57879-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="57879-112">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57879-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57879-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57879-113">Requirements</span></span>  
 <span data-ttu-id="57879-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57879-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57879-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57879-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57879-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57879-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57879-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57879-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57879-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57879-118">See also</span></span>
- [<span data-ttu-id="57879-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="57879-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="57879-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="57879-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
