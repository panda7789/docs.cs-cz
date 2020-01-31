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
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794507"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="a4388-102">ICorDebugFunction – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4388-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="a4388-103">Představuje spravovanou funkci nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="a4388-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4388-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a4388-104">Methods</span></span>  
  
|<span data-ttu-id="a4388-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-105">Method</span></span>|<span data-ttu-id="a4388-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a4388-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4388-107">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="a4388-108">Vytvoří zarážku na začátku této funkce.</span><span class="sxs-lookup"><span data-stu-id="a4388-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="a4388-109">GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="a4388-110">Získá objekt ICorDebugClass, který představuje třídu, na kterou je tato funkce členem.</span><span class="sxs-lookup"><span data-stu-id="a4388-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="a4388-111">GetCurrentVersionNumber – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="a4388-112">Získá číslo verze poslední úpravy provedené u této funkce.</span><span class="sxs-lookup"><span data-stu-id="a4388-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="a4388-113">GetILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="a4388-114">Získá kód jazyka MSIL (Microsoft Intermediate Language) pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="a4388-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="a4388-115">GetLocalVarSigToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="a4388-116">Získá token metadat pro místní proměnnou signaturu funkce, která je reprezentovaná touto instancí `ICorDebugFunction`.</span><span class="sxs-lookup"><span data-stu-id="a4388-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="a4388-117">GetModule – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="a4388-118">Získá modul, ve kterém je tato funkce definovaná.</span><span class="sxs-lookup"><span data-stu-id="a4388-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="a4388-119">GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="a4388-120">Získá nativní kód pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="a4388-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="a4388-121">GetToken – metoda</span><span class="sxs-lookup"><span data-stu-id="a4388-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="a4388-122">Získá token metadat pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="a4388-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4388-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4388-123">Remarks</span></span>  
 <span data-ttu-id="a4388-124">Rozhraní `ICorDebugFunction` nepředstavuje funkci s parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a4388-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="a4388-125">Například instance `ICorDebugFunction` by představovala `Func<T>`, ale ne `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="a4388-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="a4388-126">Chcete-li získat parametry obecného typu, zavolejte [ICorDebugILFrame2:: EnumerateTypeParameters –](icordebugilframe2-enumeratetypeparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a4388-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="a4388-127">Vztah mezi tokenem metadat metody, `mdMethodDef`a objektem `ICorDebugFunction` metody je závislý na tom, zda je povolena funkce upravit a pokračovat pro funkci:</span><span class="sxs-lookup"><span data-stu-id="a4388-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="a4388-128">Pokud funkce upravit a pokračovat není povolena pro funkci, existuje relace 1:1 mezi objektem `ICorDebugFunction` a tokenem `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="a4388-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="a4388-129">To znamená, že funkce má jeden objekt `ICorDebugFunction` a jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="a4388-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="a4388-130">Pokud je u této funkce povolená možnost upravit a pokračovat, mezi objektem `ICorDebugFunction` a tokenem `mdMethodDef` existuje vztah n:n.</span><span class="sxs-lookup"><span data-stu-id="a4388-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="a4388-131">To znamená, že funkce může mít mnoho instancí `ICorDebugFunction`, jednu pro každou verzi funkce, ale pouze jeden token `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="a4388-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4388-132">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a4388-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4388-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4388-133">Requirements</span></span>  
 <span data-ttu-id="a4388-134">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4388-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4388-135">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a4388-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4388-136">**Knihovna:**  CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a4388-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4388-137">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4388-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4388-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4388-138">See also</span></span>

- [<span data-ttu-id="a4388-139">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a4388-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
