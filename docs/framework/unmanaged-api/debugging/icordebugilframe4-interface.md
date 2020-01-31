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
ms.openlocfilehash: 7f1c5d7a6fdae3e4c5a66c9aa4a82911105f4597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788495"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="ac5bb-102">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="ac5bb-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="ac5bb-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ac5bb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ac5bb-104">Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ac5bb-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="ac5bb-105">Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="ac5bb-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac5bb-106">Metody</span><span class="sxs-lookup"><span data-stu-id="ac5bb-106">Methods</span></span>  
  
|<span data-ttu-id="ac5bb-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bb-107">Method</span></span>|<span data-ttu-id="ac5bb-108">Popis</span><span class="sxs-lookup"><span data-stu-id="ac5bb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac5bb-109">EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bb-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="ac5bb-110">Vrátí seznam místních proměnných dostupných v aktuálním rámci.</span><span class="sxs-lookup"><span data-stu-id="ac5bb-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="ac5bb-111">GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bb-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="ac5bb-112">Vrátí kód, na kterém je spuštěn tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ac5bb-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="ac5bb-113">GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ac5bb-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="ac5bb-114">Vrátí hodnotu lokální proměnné v rámci rámce IL.</span><span class="sxs-lookup"><span data-stu-id="ac5bb-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac5bb-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac5bb-115">Remarks</span></span>  
 <span data-ttu-id="ac5bb-116">Tyto metody nabízejí funkce kromě těch, které poskytují metody [EnumerateLocalVariables –](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)a [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ac5bb-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="ac5bb-117">Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další lokální proměnné nebo kód definované žádostí ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="ac5bb-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5bb-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac5bb-118">Requirements</span></span>  
 <span data-ttu-id="ac5bb-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5bb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5bb-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac5bb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac5bb-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ac5bb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac5bb-122">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5bb-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac5bb-123">See also</span></span>

- [<span data-ttu-id="ac5bb-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ac5bb-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ac5bb-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="ac5bb-125">Debugging</span></span>](index.md)
