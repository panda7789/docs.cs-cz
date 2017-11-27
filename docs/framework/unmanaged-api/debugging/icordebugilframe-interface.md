---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8d370fa971f698eb694127c72ff96499b85143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="3b240-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="3b240-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="3b240-103">Představuje rámce zásobníku kódu (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3b240-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="3b240-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="3b240-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b240-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3b240-105">Methods</span></span>  
  
|<span data-ttu-id="3b240-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-106">Method</span></span>|<span data-ttu-id="3b240-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3b240-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b240-108">Cansetip – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="3b240-109">Získá hodnotu, která určuje, zda je bezpečné nastavit ukazatel instrukce do zadaného umístění posunu.</span><span class="sxs-lookup"><span data-stu-id="3b240-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="3b240-110">Enumeratearguments – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="3b240-111">Získá enumerátor pro argumenty do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="3b240-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="3b240-112">Enumeratelocalvariables – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="3b240-113">Získá enumerátor pro místní proměnné do tohoto rámce.</span><span class="sxs-lookup"><span data-stu-id="3b240-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="3b240-114">GetArgument – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="3b240-115">Získá hodnotu zadaného argumentu v rámci této MSIL zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3b240-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3b240-116">Getip – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="3b240-117">Získá hodnotu ukazatel instrukce a bitovou kombinaci hodnotu, která popisuje, jak byla získána hodnota ukazatele instrukcí.</span><span class="sxs-lookup"><span data-stu-id="3b240-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="3b240-118">Getlocalvariable – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="3b240-119">Získá hodnotu zadaného místní proměnné v rámci této MSIL zásobníku.</span><span class="sxs-lookup"><span data-stu-id="3b240-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="3b240-120">Getstackdepth – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="3b240-121">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3b240-121">Not implemented.</span></span>|  
|[<span data-ttu-id="3b240-122">Getstackvalue – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="3b240-123">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3b240-123">Not implemented.</span></span>|  
|[<span data-ttu-id="3b240-124">Setip – metoda</span><span class="sxs-lookup"><span data-stu-id="3b240-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="3b240-125">Nastaví ukazatel instrukce do zadaného umístění posunu v MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="3b240-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b240-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b240-126">Remarks</span></span>  
 <span data-ttu-id="3b240-127">`ICorDebugILFrame` Rozhraní je specializovaná ICorDebugFrame rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3b240-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="3b240-128">Použije se buď MSIL kód rámce nebo v běhu (JIT) zkompilovat rámce.</span><span class="sxs-lookup"><span data-stu-id="3b240-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="3b240-129">Rámce kompilována implementovat i `ICorDebugILFrame` ICorDebugNativeFrame rozhraní a.</span><span class="sxs-lookup"><span data-stu-id="3b240-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b240-130">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3b240-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b240-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b240-131">Requirements</span></span>  
 <span data-ttu-id="3b240-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b240-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b240-133">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b240-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b240-134">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b240-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b240-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b240-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b240-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b240-136">See Also</span></span>  
 [<span data-ttu-id="3b240-137">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b240-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
