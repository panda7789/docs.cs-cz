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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794368"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="5714d-102">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="5714d-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="5714d-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="5714d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5714d-104">Logicky rozšiřuje rozhraní [ICorDebugILCode](icordebugilcode-interface.md) a poskytuje metody, které vracejí token pro místní proměnnou funkce a které mapují posuny instrumentované zprostředkujícího jazyka (IL) profileru na původní posunutí metody Il.</span><span class="sxs-lookup"><span data-stu-id="5714d-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5714d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5714d-105">Methods</span></span>  
  
|<span data-ttu-id="5714d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5714d-106">Method</span></span>|<span data-ttu-id="5714d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5714d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5714d-108">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="5714d-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="5714d-109">Vrátí mapu ze vah instrumentované úrovně IL v profileru na původní posunutí metody IL pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="5714d-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="5714d-110">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="5714d-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="5714d-111">Získá token metadat pro podpis místní proměnné pro funkci, která je reprezentovaná touto instancí.</span><span class="sxs-lookup"><span data-stu-id="5714d-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5714d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5714d-112">Requirements</span></span>  
 <span data-ttu-id="5714d-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5714d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5714d-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5714d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5714d-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5714d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5714d-116">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5714d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5714d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5714d-117">See also</span></span>

- [<span data-ttu-id="5714d-118">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5714d-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="5714d-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5714d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5714d-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="5714d-120">Debugging</span></span>](index.md)
