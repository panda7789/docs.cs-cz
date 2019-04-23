---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223040"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="1779c-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1779c-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="1779c-103">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="1779c-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="1779c-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="1779c-104">Method</span></span>  
  
|<span data-ttu-id="1779c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1779c-105">Method</span></span>|<span data-ttu-id="1779c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1779c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1779c-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="1779c-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="1779c-108">Získá seznam modulů, které zatím byly načteny.</span><span class="sxs-lookup"><span data-stu-id="1779c-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1779c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1779c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1779c-110">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1779c-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1779c-111">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1779c-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1779c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1779c-112">Requirements</span></span>  
 <span data-ttu-id="1779c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1779c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1779c-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1779c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1779c-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1779c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1779c-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1779c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1779c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1779c-117">See also</span></span>

- [<span data-ttu-id="1779c-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1779c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1779c-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="1779c-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
