---
title: ICorDebugModuleDebugEvent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: a2c7eaa8a2c811c1696024d9af4b715cc49e7caa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792899"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="05274-102">ICorDebugModuleDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05274-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="05274-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="05274-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05274-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05274-104">Methods</span></span>  
  
|<span data-ttu-id="05274-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05274-105">Method</span></span>|<span data-ttu-id="05274-106">Popis</span><span class="sxs-lookup"><span data-stu-id="05274-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05274-107">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="05274-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="05274-108">Získá sloučený modul, který byl právě načten nebo uvolněn.</span><span class="sxs-lookup"><span data-stu-id="05274-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05274-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05274-109">Remarks</span></span>  
 <span data-ttu-id="05274-110">Typy událostí [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05274-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05274-111">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05274-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="05274-112">Pokus o volání `QueryInterface` pro načtení ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05274-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05274-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05274-113">Requirements</span></span>  
 <span data-ttu-id="05274-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05274-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05274-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05274-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05274-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05274-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05274-117">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05274-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05274-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05274-118">See also</span></span>

- [<span data-ttu-id="05274-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="05274-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="05274-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="05274-120">Debugging</span></span>](index.md)
