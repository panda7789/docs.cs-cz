---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f97a6819c413c79eb8431c9a101249d459b0155
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545248"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="b3629-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="b3629-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="b3629-103">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="b3629-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="b3629-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3629-104">Method</span></span>  
  
|<span data-ttu-id="b3629-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3629-105">Method</span></span>|<span data-ttu-id="b3629-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b3629-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3629-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="b3629-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="b3629-108">Získá seznam modulů, které zatím byly načteny.</span><span class="sxs-lookup"><span data-stu-id="b3629-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3629-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3629-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3629-110">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b3629-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b3629-111">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3629-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3629-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3629-112">Requirements</span></span>  
 <span data-ttu-id="b3629-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3629-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3629-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3629-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3629-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3629-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3629-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3629-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3629-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3629-117">See also</span></span>
- [<span data-ttu-id="b3629-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b3629-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b3629-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="b3629-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
