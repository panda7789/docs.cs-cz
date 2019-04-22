---
title: Rozhraní ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a27dbd8b5013937bb97f37113687405c988c1fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142659"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="d7bfb-102">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="d7bfb-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="d7bfb-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d7bfb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d7bfb-104">Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.</span><span class="sxs-lookup"><span data-stu-id="d7bfb-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7bfb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d7bfb-105">Methods</span></span>  
  
|<span data-ttu-id="d7bfb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7bfb-106">Method</span></span>|<span data-ttu-id="d7bfb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d7bfb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7bfb-108">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="d7bfb-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="d7bfb-109">Vrátí že mapu z profileru instrumentována posun IL na původní metodu IL posunutí pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="d7bfb-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="d7bfb-110">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d7bfb-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="d7bfb-111">Získá token metadat pro místní proměnné podpis pro funkci, která je reprezentovaný touto instancí.</span><span class="sxs-lookup"><span data-stu-id="d7bfb-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7bfb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7bfb-112">Requirements</span></span>  
 <span data-ttu-id="d7bfb-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7bfb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7bfb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7bfb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7bfb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7bfb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7bfb-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7bfb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bfb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7bfb-117">See also</span></span>

- [<span data-ttu-id="d7bfb-118">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7bfb-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="d7bfb-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d7bfb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d7bfb-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="d7bfb-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
