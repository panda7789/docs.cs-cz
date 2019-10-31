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
ms.openlocfilehash: 9c1a5cde5a39a334d655d865c5e44a5eb0c1766a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131045"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="ddad5-102">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="ddad5-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="ddad5-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ddad5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ddad5-104">Logicky rozšiřuje rozhraní [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) a poskytuje metody, které vracejí token pro místní proměnnou funkce a které mapují posuny instrumentované zprostředkujícího jazyka (IL) profileru na původní posunutí metody Il.</span><span class="sxs-lookup"><span data-stu-id="ddad5-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ddad5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ddad5-105">Methods</span></span>  
  
|<span data-ttu-id="ddad5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ddad5-106">Method</span></span>|<span data-ttu-id="ddad5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ddad5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ddad5-108">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="ddad5-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="ddad5-109">Vrátí mapu ze vah instrumentované úrovně IL v profileru na původní posunutí metody IL pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="ddad5-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="ddad5-110">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="ddad5-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="ddad5-111">Získá token metadat pro podpis místní proměnné pro funkci, která je reprezentovaná touto instancí.</span><span class="sxs-lookup"><span data-stu-id="ddad5-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ddad5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddad5-112">Requirements</span></span>  
 <span data-ttu-id="ddad5-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddad5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddad5-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ddad5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddad5-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ddad5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddad5-116">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddad5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddad5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddad5-117">See also</span></span>

- [<span data-ttu-id="ddad5-118">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddad5-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="ddad5-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ddad5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ddad5-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="ddad5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
