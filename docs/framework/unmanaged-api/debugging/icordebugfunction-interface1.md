---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="d1469-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="d1469-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="d1469-103">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="d1469-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1469-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d1469-104">Methods</span></span>  
  
|<span data-ttu-id="d1469-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-105">Method</span></span>|<span data-ttu-id="d1469-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d1469-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1469-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="d1469-108">Vytvoří zarážku na začátku této funkce.</span><span class="sxs-lookup"><span data-stu-id="d1469-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="d1469-109">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="d1469-110">Získá objekt ICorDebugClass, který představuje třídu, ke které tato funkce je členem skupiny.</span><span class="sxs-lookup"><span data-stu-id="d1469-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="d1469-111">GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="d1469-112">Získá číslo verze nejnovější úpravy provedené v této funkce.</span><span class="sxs-lookup"><span data-stu-id="d1469-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="d1469-113">GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="d1469-114">Získá kód (MSIL intermediate language) společnosti Microsoft pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d1469-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="d1469-115">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="d1469-116">Získá token metadata pro místní proměnné podpis funkce, která je reprezentována to `ICorDebugFunction` instance.</span><span class="sxs-lookup"><span data-stu-id="d1469-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="d1469-117">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="d1469-118">Získá modul, ve kterém je definována funkce.</span><span class="sxs-lookup"><span data-stu-id="d1469-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="d1469-119">GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="d1469-120">Získá nativní kód pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d1469-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="d1469-121">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d1469-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="d1469-122">Získá token metadata pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d1469-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1469-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1469-123">Remarks</span></span>  
 <span data-ttu-id="d1469-124">`ICorDebugFunction` Rozhraní nepředstavuje funkce s parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d1469-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="d1469-125">Například `ICorDebugFunction` instance by představují `Func<T>` ale ne `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="d1469-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="d1469-126">Volání [icordebugilframe2::enumeratetypeparameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) získat parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d1469-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="d1469-127">Vztah mezi metodu na token metadata, `mdMethodDef`a metody `ICorDebugFunction` objektu je závislá na povolení upravit a pokračovat na funkci:</span><span class="sxs-lookup"><span data-stu-id="d1469-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="d1469-128">Je-li upravit a pokračovat není povolena pro funkci, mezi existuje relace 1: 1 `ICorDebugFunction` objektu a `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1469-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="d1469-129">To znamená, funkce má jeden `ICorDebugFunction` objektů a jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1469-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="d1469-130">Pokud upravit a pokračovat, je povolena pro funkci, mezi existuje relace n: 1 `ICorDebugFunction` objektu a `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1469-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="d1469-131">To znamená, funkce může obsahovat mnoho instancí `ICorDebugFunction`, jedna pro každou verzi funkce, ale pouze jedna `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="d1469-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1469-132">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d1469-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1469-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1469-133">Requirements</span></span>  
 <span data-ttu-id="d1469-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1469-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1469-135">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1469-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1469-136">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1469-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1469-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1469-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1469-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1469-138">See Also</span></span>  
 [<span data-ttu-id="d1469-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d1469-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
