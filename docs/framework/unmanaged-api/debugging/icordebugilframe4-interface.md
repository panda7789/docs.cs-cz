---
title: "Rozhraní ICorDebugILFrame4"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame4
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b42a2ed4e93fd5e4c662bab34b111fe0757890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="ce977-102">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="ce977-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="ce977-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ce977-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ce977-104">Poskytuje metody, které vám umožní přístup k místní proměnné a kódu v zásobníku kódu převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="ce977-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="ce977-105">Parametr určuje, zda ladicí program má přístup k proměnné a kódu přidaném v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="ce977-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce977-106">Metody</span><span class="sxs-lookup"><span data-stu-id="ce977-106">Methods</span></span>  
  
|<span data-ttu-id="ce977-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="ce977-107">Method</span></span>|<span data-ttu-id="ce977-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ce977-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce977-109">Metoda EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="ce977-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="ce977-110">Vrátí seznam hodnot lokální proměnné, které jsou dostupné v aktuálním snímku.</span><span class="sxs-lookup"><span data-stu-id="ce977-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="ce977-111">Metoda GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="ce977-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="ce977-112">Vrátí kód, který je spuštěn tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ce977-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="ce977-113">Metoda GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="ce977-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="ce977-114">Vrátí hodnotu místní proměnné v rámci IL.</span><span class="sxs-lookup"><span data-stu-id="ce977-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce977-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce977-115">Remarks</span></span>  
 <span data-ttu-id="ce977-116">Tyto metody nabízejí funkce k těm, které poskytuje [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), a [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ce977-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="ce977-117">Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další místní proměnné nebo kód definované profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="ce977-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce977-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce977-118">Requirements</span></span>  
 <span data-ttu-id="ce977-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce977-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce977-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce977-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce977-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce977-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce977-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce977-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce977-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce977-123">See Also</span></span>  
 [<span data-ttu-id="ce977-124">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce977-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ce977-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="ce977-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
