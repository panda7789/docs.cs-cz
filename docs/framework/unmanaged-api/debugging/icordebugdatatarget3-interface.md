---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965201"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="f0477-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="f0477-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="f0477-103">Logicky rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro zadání informací o načtené moduly.</span><span class="sxs-lookup"><span data-stu-id="f0477-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="f0477-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0477-104">Method</span></span>  
  
|<span data-ttu-id="f0477-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0477-105">Method</span></span>|<span data-ttu-id="f0477-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f0477-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0477-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="f0477-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="f0477-108">Získá seznam modulů, které zatím byly načteny.</span><span class="sxs-lookup"><span data-stu-id="f0477-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0477-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0477-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0477-110">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0477-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f0477-111">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f0477-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0477-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0477-112">Requirements</span></span>  
 <span data-ttu-id="f0477-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0477-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0477-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0477-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0477-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0477-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0477-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0477-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0477-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f0477-117">See also</span></span>

- [<span data-ttu-id="f0477-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f0477-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f0477-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="f0477-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
