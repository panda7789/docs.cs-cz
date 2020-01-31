---
title: ICorDebugILFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788581"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="193e1-102">ICorDebugILFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="193e1-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="193e1-103">Představuje rámec zásobníku kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="193e1-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="193e1-104">Toto rozhraní je podtřídou rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="193e1-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="193e1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="193e1-105">Methods</span></span>  
  
|<span data-ttu-id="193e1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-106">Method</span></span>|<span data-ttu-id="193e1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="193e1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="193e1-108">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="193e1-109">Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na určené místo posunutí.</span><span class="sxs-lookup"><span data-stu-id="193e1-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="193e1-110">EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="193e1-111">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="193e1-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="193e1-112">EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="193e1-113">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="193e1-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="193e1-114">GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="193e1-115">Získá hodnotu zadaného argumentu v rámci tohoto bloku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="193e1-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="193e1-116">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="193e1-117">Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="193e1-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="193e1-118">GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="193e1-119">Získá hodnotu zadané místní proměnné v tomto bloku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="193e1-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="193e1-120">GetStackDepth – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="193e1-121">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="193e1-121">Not implemented.</span></span>|  
|[<span data-ttu-id="193e1-122">GetStackValue – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="193e1-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="193e1-123">Not implemented.</span></span>|  
|[<span data-ttu-id="193e1-124">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="193e1-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="193e1-125">Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="193e1-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="193e1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="193e1-126">Remarks</span></span>  
 <span data-ttu-id="193e1-127">Rozhraní `ICorDebugILFrame` je specializované rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="193e1-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="193e1-128">Používá se buď pro rámečky kódu MSIL, nebo pro zkompilované snímky JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="193e1-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="193e1-129">Rámce zkompilované JIT implementují rozhraní `ICorDebugILFrame` i rozhraní ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="193e1-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="193e1-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="193e1-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="193e1-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="193e1-131">Requirements</span></span>  
 <span data-ttu-id="193e1-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="193e1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="193e1-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="193e1-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="193e1-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="193e1-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="193e1-135">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="193e1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193e1-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="193e1-136">See also</span></span>

- [<span data-ttu-id="193e1-137">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="193e1-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
