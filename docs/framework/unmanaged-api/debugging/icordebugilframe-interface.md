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
ms.openlocfilehash: 1f1e42cd929d2d6282d282cf62dce00104b3a925
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210238"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="895be-102">ICorDebugILFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="895be-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="895be-103">Představuje rámec zásobníku kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="895be-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="895be-104">Toto rozhraní je podtřídou rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="895be-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="895be-105">Metody</span><span class="sxs-lookup"><span data-stu-id="895be-105">Methods</span></span>  
  
|<span data-ttu-id="895be-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="895be-106">Method</span></span>|<span data-ttu-id="895be-107">Popis</span><span class="sxs-lookup"><span data-stu-id="895be-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="895be-108">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="895be-109">Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na určené místo posunutí.</span><span class="sxs-lookup"><span data-stu-id="895be-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="895be-110">EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="895be-111">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="895be-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="895be-112">EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="895be-113">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="895be-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="895be-114">GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="895be-115">Získá hodnotu zadaného argumentu v rámci tohoto bloku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="895be-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="895be-116">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="895be-117">Získá hodnotu ukazatele na instrukci a bitovou kombinaci hodnoty, která popisuje, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="895be-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="895be-118">GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="895be-119">Získá hodnotu zadané místní proměnné v tomto bloku zásobníku MSIL.</span><span class="sxs-lookup"><span data-stu-id="895be-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="895be-120">GetStackDepth – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="895be-121">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="895be-121">Not implemented.</span></span>|  
|[<span data-ttu-id="895be-122">GetStackValue – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="895be-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="895be-123">Not implemented.</span></span>|  
|[<span data-ttu-id="895be-124">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="895be-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="895be-125">Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="895be-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="895be-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="895be-126">Remarks</span></span>  
 <span data-ttu-id="895be-127">`ICorDebugILFrame`Rozhraní je specializované rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="895be-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="895be-128">Používá se buď pro rámečky kódu MSIL, nebo pro zkompilované snímky JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="895be-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="895be-129">Rámce zkompilované JIT implementují `ICorDebugILFrame` rozhraní i rozhraní ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="895be-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="895be-130">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="895be-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="895be-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="895be-131">Requirements</span></span>  
 <span data-ttu-id="895be-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="895be-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="895be-133">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="895be-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="895be-134">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="895be-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="895be-135">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="895be-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895be-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="895be-136">See also</span></span>

- [<span data-ttu-id="895be-137">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="895be-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
