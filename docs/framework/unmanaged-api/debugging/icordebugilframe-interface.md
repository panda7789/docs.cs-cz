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
ms.openlocfilehash: 4a97704e00278e19181df569f108f428cb1ec90f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417742"
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="c124b-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="c124b-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="c124b-103">Představuje rámce zásobníku kódu (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c124b-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="c124b-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="c124b-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c124b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c124b-105">Methods</span></span>  
  
|<span data-ttu-id="c124b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-106">Method</span></span>|<span data-ttu-id="c124b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c124b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c124b-108">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="c124b-109">Získá hodnotu, která určuje, zda je bezpečné nastavit ukazatel instrukce do zadaného umístění posunu.</span><span class="sxs-lookup"><span data-stu-id="c124b-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="c124b-110">EnumerateArguments – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="c124b-111">Získá enumerátor pro argumenty do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="c124b-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="c124b-112">EnumerateLocalVariables – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="c124b-113">Získá enumerátor pro místní proměnné do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="c124b-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="c124b-114">GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="c124b-115">Získá hodnotu zadaného argumentu v rámci této MSIL zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c124b-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="c124b-116">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="c124b-117">Získá hodnotu ukazatel instrukce a bitovou kombinaci hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="c124b-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="c124b-118">GetLocalVariable – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="c124b-119">Získá hodnotu zadaného místní proměnné v rámci této MSIL zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c124b-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="c124b-120">GetStackDepth – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="c124b-121">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="c124b-121">Not implemented.</span></span>|  
|[<span data-ttu-id="c124b-122">GetStackValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="c124b-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="c124b-123">Not implemented.</span></span>|  
|[<span data-ttu-id="c124b-124">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c124b-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="c124b-125">Nastaví ukazatel instrukce do zadaného umístění posunu v MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="c124b-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c124b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c124b-126">Remarks</span></span>  
 <span data-ttu-id="c124b-127">`ICorDebugILFrame` Rozhraní je specializovaná ICorDebugFrame rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c124b-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="c124b-128">Použije se buď MSIL kód rámce nebo v běhu (JIT) zkompilovat rámce.</span><span class="sxs-lookup"><span data-stu-id="c124b-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="c124b-129">Rámce kompilována implementovat i `ICorDebugILFrame` ICorDebugNativeFrame rozhraní a.</span><span class="sxs-lookup"><span data-stu-id="c124b-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c124b-130">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c124b-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c124b-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c124b-131">Requirements</span></span>  
 <span data-ttu-id="c124b-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c124b-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c124b-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c124b-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c124b-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c124b-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c124b-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c124b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c124b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="c124b-136">See Also</span></span>  
 [<span data-ttu-id="c124b-137">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c124b-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
