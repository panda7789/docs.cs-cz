---
title: ICorDebugFunction – rozhraní
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
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917205"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="fcdb0-102">ICorDebugFunction – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcdb0-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="fcdb0-103">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fcdb0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fcdb0-104">Methods</span></span>  
  
|<span data-ttu-id="fcdb0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-105">Method</span></span>|<span data-ttu-id="fcdb0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fcdb0-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="fcdb0-108">Vytvoří zarážku na začátku této funkce.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="fcdb0-109">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="fcdb0-110">Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="fcdb0-111">GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="fcdb0-112">Získá číslo verze poslední úpravy provedené u této funkce.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="fcdb0-113">GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="fcdb0-114">Získá kód jazyka MSIL (Microsoft Intermediate Language) pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="fcdb0-115">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="fcdb0-116">Získá token metadat pro podpis místní proměnné funkce, která je reprezentovaná touto `ICorDebugFunction` instancí.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="fcdb0-117">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="fcdb0-118">Získá modul, ve kterém je tato funkce definovaná.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="fcdb0-119">GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="fcdb0-120">Získá nativní kód pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="fcdb0-121">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="fcdb0-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="fcdb0-122">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcdb0-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcdb0-123">Remarks</span></span>  
 <span data-ttu-id="fcdb0-124">`ICorDebugFunction` Rozhraní nepředstavuje funkci s parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="fcdb0-125">Například `ICorDebugFunction` instance by představovala `Func<T>` , ale ne `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="fcdb0-126">Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fcdb0-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="fcdb0-127">Vztah mezi tokenem metadat metody, `mdMethodDef`a `ICorDebugFunction` objektem metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:</span><span class="sxs-lookup"><span data-stu-id="fcdb0-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="fcdb0-128">Pokud funkce upravit a pokračovat není u této funkce povolená, relace 1:1 mezi `ICorDebugFunction` objektem `mdMethodDef` a tokenem existuje.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="fcdb0-129">To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="fcdb0-130">Pokud je u této funkce povolená možnost upravit a pokračovat, existuje relace n:n mezi `ICorDebugFunction` objektem `mdMethodDef` a tokenem.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="fcdb0-131">To znamená, že funkce může mít mnoho instancí `ICorDebugFunction`, jednu pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcdb0-132">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fcdb0-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcdb0-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcdb0-133">Requirements</span></span>  
 <span data-ttu-id="fcdb0-134">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcdb0-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcdb0-135">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fcdb0-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcdb0-136">**Knihovna**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcdb0-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcdb0-137">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcdb0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcdb0-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcdb0-138">See also</span></span>

- [<span data-ttu-id="fcdb0-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fcdb0-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
