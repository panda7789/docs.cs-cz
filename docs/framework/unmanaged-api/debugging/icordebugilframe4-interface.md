---
title: Rozhraní ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b57289e1d96a56bc4ab5cb8c07cbcac4b1d98b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416576"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="e9a8e-102">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="e9a8e-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="e9a8e-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e9a8e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e9a8e-104">Poskytuje metody, které vám umožní přístup k místní proměnné a kódu v zásobníku kódu převodní jazyk (IL).</span><span class="sxs-lookup"><span data-stu-id="e9a8e-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="e9a8e-105">Parametr určuje, zda ladicí program má přístup k proměnné a kódu přidaném v ReJIT instrumentace profileru.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9a8e-106">Metody</span><span class="sxs-lookup"><span data-stu-id="e9a8e-106">Methods</span></span>  
  
|<span data-ttu-id="e9a8e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9a8e-107">Method</span></span>|<span data-ttu-id="e9a8e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e9a8e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9a8e-109">EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e9a8e-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="e9a8e-110">Vrátí seznam hodnot lokální proměnné, které jsou dostupné v aktuálním snímku.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="e9a8e-111">GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e9a8e-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="e9a8e-112">Vrátí kód, který je spuštěn tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="e9a8e-113">GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="e9a8e-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="e9a8e-114">Vrátí hodnotu místní proměnné v rámci IL.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a8e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9a8e-115">Remarks</span></span>  
 <span data-ttu-id="e9a8e-116">Tyto metody nabízejí funkce k těm, které poskytuje [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), a [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="e9a8e-117">Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další místní proměnné nebo kód definované profileru ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="e9a8e-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a8e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9a8e-118">Requirements</span></span>  
 <span data-ttu-id="e9a8e-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a8e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a8e-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9a8e-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9a8e-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9a8e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a8e-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a8e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a8e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9a8e-123">See Also</span></span>  
 [<span data-ttu-id="e9a8e-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e9a8e-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e9a8e-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="e9a8e-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
