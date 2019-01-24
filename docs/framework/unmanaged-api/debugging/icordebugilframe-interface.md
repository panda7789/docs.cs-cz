---
title: ICorDebugILFrame Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73cf7f26b228fa5aa458a6de312df3bf777e0206
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580509"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="3575a-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="3575a-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="3575a-103">Představuje rámec zásobníku kódu Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="3575a-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="3575a-104">Toto rozhraní je podtřídou třídy icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3575a-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3575a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3575a-105">Methods</span></span>  
  
|<span data-ttu-id="3575a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-106">Method</span></span>|<span data-ttu-id="3575a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3575a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3575a-108">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="3575a-109">Získá hodnotu, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu.</span><span class="sxs-lookup"><span data-stu-id="3575a-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="3575a-110">EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="3575a-111">Získá enumerátor pro argumenty v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="3575a-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="3575a-112">EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="3575a-113">Získá enumerátor pro místní proměnné v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="3575a-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="3575a-114">GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="3575a-115">Získá hodnotu zadaného argumentu do tohoto rámce zásobníku jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="3575a-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3575a-116">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="3575a-117">Získá hodnotu ukazatele na instrukci a bitová kombinace hodnotu, která popisuje, jak byla získána hodnota ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="3575a-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="3575a-118">GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="3575a-119">Získá hodnotu místní proměnné zadané v rámce zásobníku jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="3575a-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3575a-120">GetStackDepth – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="3575a-121">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3575a-121">Not implemented.</span></span>|  
|[<span data-ttu-id="3575a-122">GetStackValue – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="3575a-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3575a-123">Not implemented.</span></span>|  
|[<span data-ttu-id="3575a-124">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="3575a-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="3575a-125">Nastaví ukazatele na instrukci do zadaného umístění posunu v kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="3575a-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3575a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3575a-126">Remarks</span></span>  
 <span data-ttu-id="3575a-127">`ICorDebugILFrame` Rozhraní je specializované icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3575a-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="3575a-128">Používá se pro snímky kód jazyka MSIL nebo just-in-time (JIT) zkompilována snímků.</span><span class="sxs-lookup"><span data-stu-id="3575a-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="3575a-129">Snímky zkompilovaný pomocí kompilátoru JIT implementovat oba `ICorDebugILFrame` icordebugnativeframe – rozhraní a interface.</span><span class="sxs-lookup"><span data-stu-id="3575a-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3575a-130">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="3575a-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3575a-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3575a-131">Requirements</span></span>  
 <span data-ttu-id="3575a-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3575a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3575a-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3575a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3575a-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3575a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3575a-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3575a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3575a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3575a-136">See also</span></span>
- [<span data-ttu-id="3575a-137">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3575a-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
