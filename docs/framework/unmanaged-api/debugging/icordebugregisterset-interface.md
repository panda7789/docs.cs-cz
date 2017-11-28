---
title: "ICorDebugRegisterSet – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="06daf-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06daf-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="06daf-103">Představuje sadu registrů, k dispozici v počítači, který je aktuálně provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="06daf-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06daf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06daf-104">Methods</span></span>  
  
|<span data-ttu-id="06daf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-105">Method</span></span>|<span data-ttu-id="06daf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="06daf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06daf-107">Getregisters – metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="06daf-108">Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.</span><span class="sxs-lookup"><span data-stu-id="06daf-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="06daf-109">Getregistersavailable – metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="06daf-110">Získá trochu maskování, která určuje, který registruje v tomto `ICorDebugRegisterSet` jsou nyní k dispozici.</span><span class="sxs-lookup"><span data-stu-id="06daf-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="06daf-111">Getthreadcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="06daf-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="06daf-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="06daf-113">Setregisters – metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="06daf-114">Není implementována pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="06daf-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="06daf-115">Setthreadcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="06daf-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="06daf-116">Není implementována pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="06daf-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06daf-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06daf-117">Remarks</span></span>  
 <span data-ttu-id="06daf-118">`ICorDebugRegisterSet` Rozhraní podporuje pouze 32bitové registry.</span><span class="sxs-lookup"><span data-stu-id="06daf-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="06daf-119">Použití [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) rozhraní na platformách, které vyžadují další registrů, například IA-64.</span><span class="sxs-lookup"><span data-stu-id="06daf-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06daf-120">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="06daf-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06daf-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06daf-121">Requirements</span></span>  
 <span data-ttu-id="06daf-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06daf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06daf-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06daf-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06daf-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06daf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06daf-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06daf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06daf-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="06daf-126">See Also</span></span>  
 [<span data-ttu-id="06daf-127">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="06daf-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="06daf-128">ICorDebugRegisterSet2 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="06daf-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
