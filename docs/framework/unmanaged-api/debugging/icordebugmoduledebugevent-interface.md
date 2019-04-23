---
title: ICorDebugModuleDebugEvent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160911"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="81d9c-102">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81d9c-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="81d9c-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="81d9c-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81d9c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="81d9c-104">Methods</span></span>  
  
|<span data-ttu-id="81d9c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="81d9c-105">Method</span></span>|<span data-ttu-id="81d9c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="81d9c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81d9c-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="81d9c-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="81d9c-108">Získá sloučené modul, který byl právě nenačetl nebo je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="81d9c-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81d9c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81d9c-109">Remarks</span></span>  
 <span data-ttu-id="81d9c-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) toto rozhraní implementují typy událostí.</span><span class="sxs-lookup"><span data-stu-id="81d9c-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81d9c-111">Rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81d9c-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="81d9c-112">Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81d9c-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81d9c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81d9c-113">Requirements</span></span>  
 <span data-ttu-id="81d9c-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81d9c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81d9c-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81d9c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81d9c-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81d9c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81d9c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81d9c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d9c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81d9c-118">See also</span></span>

- [<span data-ttu-id="81d9c-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="81d9c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="81d9c-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="81d9c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
