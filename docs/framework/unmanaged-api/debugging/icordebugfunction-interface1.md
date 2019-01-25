---
title: ICorDebugFunction – rozhraní 1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b810ce8634781438faccac25f96442624a78ea0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676767"
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="63215-102">ICorDebugFunction – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="63215-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="63215-103">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="63215-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63215-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63215-104">Methods</span></span>  
  
|<span data-ttu-id="63215-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63215-105">Method</span></span>|<span data-ttu-id="63215-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63215-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63215-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="63215-108">Vytvoří zarážku na začátku této funkce.</span><span class="sxs-lookup"><span data-stu-id="63215-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="63215-109">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="63215-110">Získá ICorDebugClass objekt, který představuje třídu, tato funkce je členem skupiny.</span><span class="sxs-lookup"><span data-stu-id="63215-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="63215-111">GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="63215-112">Získá číslo verze nejnovější úpravy provedené v této funkce.</span><span class="sxs-lookup"><span data-stu-id="63215-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="63215-113">GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="63215-114">Získá kód Microsoft intermediate language (MSIL) pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="63215-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="63215-115">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="63215-116">Získá metadata pro místní proměnné podpis funkce, která je reprezentována tento token `ICorDebugFunction` instance.</span><span class="sxs-lookup"><span data-stu-id="63215-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="63215-117">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="63215-118">Získá modul, ve kterém je definována funkce.</span><span class="sxs-lookup"><span data-stu-id="63215-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="63215-119">GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="63215-120">Získá nativní kód pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="63215-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="63215-121">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="63215-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="63215-122">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="63215-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63215-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63215-123">Remarks</span></span>  
 <span data-ttu-id="63215-124">`ICorDebugFunction` Rozhraní nepředstavuje funkce s parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="63215-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="63215-125">Například `ICorDebugFunction` představuje instanci `Func<T>` , ale ne `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="63215-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="63215-126">Volání [icordebugilframe2::enumeratetypeparameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) zobrazíte parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="63215-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="63215-127">Vztah mezi tokenu metadat metodu, `mdMethodDef`a metody `ICorDebugFunction` objektu je závislá na Určuje, zda je povoleno upravit a pokračovat na funkci:</span><span class="sxs-lookup"><span data-stu-id="63215-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="63215-128">Pokud funkce upravit a pokračovat není povoleno ve funkci, po jejím obnovení relace existuje mezi `ICorDebugFunction` objektu a `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="63215-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="63215-129">To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="63215-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="63215-130">Pokud je povoleno upravit a pokračovat na funkce, mezi existuje vztah mnoha k jednomu jinému `ICorDebugFunction` objektu a `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="63215-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="63215-131">To znamená, funkce může mít mnoho instancí `ICorDebugFunction`, jeden pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="63215-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63215-132">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="63215-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63215-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63215-133">Requirements</span></span>  
 <span data-ttu-id="63215-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63215-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63215-135">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63215-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63215-136">**Knihovna:**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63215-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="63215-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63215-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63215-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63215-138">See also</span></span>
- [<span data-ttu-id="63215-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="63215-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
