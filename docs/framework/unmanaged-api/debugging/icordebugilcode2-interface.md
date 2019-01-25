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
ms.openlocfilehash: d511999cac312c785e528cda24c215555a62ae76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491165"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="17f55-102">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="17f55-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="17f55-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="17f55-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="17f55-104">Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytuje metody, které vracejí token pro místní proměnné podpis funkce a, která mapují profiler instrumentované (IL intermediate language) kompenzuje původní metody IL posuny.</span><span class="sxs-lookup"><span data-stu-id="17f55-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17f55-105">Metody</span><span class="sxs-lookup"><span data-stu-id="17f55-105">Methods</span></span>  
  
|<span data-ttu-id="17f55-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="17f55-106">Method</span></span>|<span data-ttu-id="17f55-107">Popis</span><span class="sxs-lookup"><span data-stu-id="17f55-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17f55-108">GetInstrumentedILMap – metoda</span><span class="sxs-lookup"><span data-stu-id="17f55-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="17f55-109">Vrátí že mapu z profileru instrumentována posun IL na původní metodu IL posunutí pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="17f55-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="17f55-110">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="17f55-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="17f55-111">Získá token metadat pro místní proměnné podpis pro funkci, která je reprezentovaný touto instancí.</span><span class="sxs-lookup"><span data-stu-id="17f55-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17f55-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17f55-112">Requirements</span></span>  
 <span data-ttu-id="17f55-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17f55-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17f55-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17f55-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17f55-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17f55-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17f55-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17f55-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f55-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17f55-117">See also</span></span>
- [<span data-ttu-id="17f55-118">ICorDebugILCode – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17f55-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="17f55-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="17f55-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="17f55-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="17f55-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
