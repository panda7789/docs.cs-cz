---
title: "Rozhraní ICorDebugILCode2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fd6b7b6b097010a307abbc260cda7c4b73e0f00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="1366f-102">Rozhraní ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="1366f-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="1366f-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="1366f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1366f-104">Logicky rozšiřuje [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) rozhraní poskytují metody, které vracejí token pro podpis místní proměnné funkce a která mapování profileru instrumentovaného převodní jazyk (IL) posune metodě původní IL Posune.</span><span class="sxs-lookup"><span data-stu-id="1366f-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1366f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1366f-105">Methods</span></span>  
  
|<span data-ttu-id="1366f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1366f-106">Method</span></span>|<span data-ttu-id="1366f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1366f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1366f-108">Metoda GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="1366f-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="1366f-109">Vrátí že mapu z profileru instrumentovány IL posuny k původní metoda IL posunutí pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="1366f-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="1366f-110">Getlocalvarsigtoken – metoda</span><span class="sxs-lookup"><span data-stu-id="1366f-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="1366f-111">Získá metadata token pro místní proměnné podpis pro funkce, která je reprezentována této instance.</span><span class="sxs-lookup"><span data-stu-id="1366f-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1366f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1366f-112">Requirements</span></span>  
 <span data-ttu-id="1366f-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1366f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1366f-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1366f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1366f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1366f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1366f-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1366f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1366f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1366f-117">See Also</span></span>  
 [<span data-ttu-id="1366f-118">Rozhraní ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="1366f-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="1366f-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="1366f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1366f-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="1366f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
