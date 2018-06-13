---
title: ICorDebugModuleDebugEvent rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f35c26b98521311267a627265f2dae8fa9e333de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421837"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="3e7b2-102">ICorDebugModuleDebugEvent rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e7b2-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="3e7b2-103">Rozšiřuje [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) rozhraní pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="3e7b2-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e7b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3e7b2-104">Methods</span></span>  
  
|<span data-ttu-id="3e7b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e7b2-105">Method</span></span>|<span data-ttu-id="3e7b2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3e7b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e7b2-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="3e7b2-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="3e7b2-108">Získá sloučené modul, který byl právě nenačetl nebo je odpojen.</span><span class="sxs-lookup"><span data-stu-id="3e7b2-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e7b2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e7b2-109">Remarks</span></span>  
 <span data-ttu-id="3e7b2-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) typů událostí toto rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="3e7b2-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e7b2-111">Rozhraní je k dispozici s .NET Native pouze.</span><span class="sxs-lookup"><span data-stu-id="3e7b2-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="3e7b2-112">Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3e7b2-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7b2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e7b2-113">Requirements</span></span>  
 <span data-ttu-id="3e7b2-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7b2-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e7b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e7b2-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e7b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e7b2-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e7b2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7b2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e7b2-118">See Also</span></span>  
 [<span data-ttu-id="3e7b2-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3e7b2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3e7b2-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="3e7b2-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
