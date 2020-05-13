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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213235"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="93552-102">ICorDebugFunction – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93552-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="93552-103">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="93552-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93552-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93552-104">Methods</span></span>  
  
|<span data-ttu-id="93552-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93552-105">Method</span></span>|<span data-ttu-id="93552-106">Popis</span><span class="sxs-lookup"><span data-stu-id="93552-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93552-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="93552-108">Vytvoří zarážku na začátku této funkce.</span><span class="sxs-lookup"><span data-stu-id="93552-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="93552-109">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="93552-110">Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.</span><span class="sxs-lookup"><span data-stu-id="93552-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="93552-111">GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="93552-112">Získá číslo verze poslední úpravy provedené u této funkce.</span><span class="sxs-lookup"><span data-stu-id="93552-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="93552-113">GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="93552-114">Získá kód jazyka MSIL (Microsoft Intermediate Language) pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="93552-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="93552-115">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="93552-116">Získá token metadat pro podpis místní proměnné funkce, která je reprezentovaná touto `ICorDebugFunction` instancí.</span><span class="sxs-lookup"><span data-stu-id="93552-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="93552-117">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="93552-118">Získá modul, ve kterém je tato funkce definovaná.</span><span class="sxs-lookup"><span data-stu-id="93552-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="93552-119">GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="93552-120">Získá nativní kód pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="93552-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="93552-121">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="93552-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="93552-122">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="93552-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93552-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93552-123">Remarks</span></span>  
 <span data-ttu-id="93552-124">`ICorDebugFunction`Rozhraní nepředstavuje funkci s parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="93552-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="93552-125">Například `ICorDebugFunction` instance by představovala, `Func<T>` ale ne `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="93552-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="93552-126">Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](icordebugilframe2-enumeratetypeparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93552-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="93552-127">Vztah mezi tokenem metadat metody, `mdMethodDef` a `ICorDebugFunction` objektem metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:</span><span class="sxs-lookup"><span data-stu-id="93552-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="93552-128">Pokud funkce upravit a pokračovat není u této funkce povolená, relace 1:1 mezi `ICorDebugFunction` objektem a `mdMethodDef` tokenem existuje.</span><span class="sxs-lookup"><span data-stu-id="93552-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="93552-129">To znamená, že funkce má jeden `ICorDebugFunction` objekt a jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="93552-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="93552-130">Pokud je u této funkce povolená možnost upravit a pokračovat, existuje relace n:n mezi `ICorDebugFunction` objektem a `mdMethodDef` tokenem.</span><span class="sxs-lookup"><span data-stu-id="93552-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="93552-131">To znamená, že funkce může mít mnoho instancí `ICorDebugFunction` , jednu pro každou verzi funkce, ale pouze jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="93552-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93552-132">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="93552-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93552-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93552-133">Requirements</span></span>  
 <span data-ttu-id="93552-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93552-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93552-135">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93552-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93552-136">**Knihovna:**  CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93552-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="93552-137">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93552-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93552-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="93552-138">See also</span></span>

- [<span data-ttu-id="93552-139">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93552-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
