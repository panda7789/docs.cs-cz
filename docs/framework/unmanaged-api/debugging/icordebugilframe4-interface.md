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
ms.openlocfilehash: d0b1c31d45efea4892182c43c801112530361994
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213699"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="2158a-102">Rozhraní ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="2158a-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="2158a-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="2158a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2158a-104">Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="2158a-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="2158a-105">Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="2158a-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2158a-106">Metody</span><span class="sxs-lookup"><span data-stu-id="2158a-106">Methods</span></span>  
  
|<span data-ttu-id="2158a-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="2158a-107">Method</span></span>|<span data-ttu-id="2158a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2158a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2158a-109">EnumerateLocalVariablesEx – metoda</span><span class="sxs-lookup"><span data-stu-id="2158a-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="2158a-110">Vrátí seznam místních proměnných dostupných v aktuálním rámci.</span><span class="sxs-lookup"><span data-stu-id="2158a-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="2158a-111">GetCodeEx – metoda</span><span class="sxs-lookup"><span data-stu-id="2158a-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="2158a-112">Vrátí kód, na kterém je spuštěn tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2158a-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="2158a-113">GetLocalVariableEx – metoda</span><span class="sxs-lookup"><span data-stu-id="2158a-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="2158a-114">Vrátí hodnotu lokální proměnné v rámci rámce IL.</span><span class="sxs-lookup"><span data-stu-id="2158a-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2158a-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2158a-115">Remarks</span></span>  
 <span data-ttu-id="2158a-116">Tyto metody nabízejí funkce kromě těch, které poskytují metody [EnumerateLocalVariables –](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)a [GetLocalVariable –](icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2158a-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="2158a-117">Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další lokální proměnné nebo kód definované žádostí ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="2158a-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2158a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2158a-118">Requirements</span></span>  
 <span data-ttu-id="2158a-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2158a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2158a-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2158a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2158a-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2158a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2158a-122">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2158a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2158a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2158a-123">See also</span></span>

- [<span data-ttu-id="2158a-124">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2158a-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2158a-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="2158a-125">Debugging</span></span>](index.md)
