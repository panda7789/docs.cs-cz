---
title: ICorDebugRegisterSet – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b0a5d80d984a3c696b178c4d8c936bd47354945
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135236"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="90796-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90796-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="90796-103">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="90796-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90796-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90796-104">Methods</span></span>  
  
|<span data-ttu-id="90796-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90796-105">Method</span></span>|<span data-ttu-id="90796-106">Popis</span><span class="sxs-lookup"><span data-stu-id="90796-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90796-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="90796-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="90796-108">Získá hodnotu každý registr (na počítači, který aktuálně spouští kód), která je určená bitová maska.</span><span class="sxs-lookup"><span data-stu-id="90796-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="90796-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="90796-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="90796-110">Získá o něco maskování určující, který registruje v tomto `ICorDebugRegisterSet` jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="90796-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="90796-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="90796-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="90796-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="90796-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="90796-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="90796-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="90796-114">Není implementováno pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="90796-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="90796-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="90796-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="90796-116">Není implementováno pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="90796-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90796-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90796-117">Remarks</span></span>  
 <span data-ttu-id="90796-118">`ICorDebugRegisterSet` Rozhraní podporuje pouze 32bitové registrů.</span><span class="sxs-lookup"><span data-stu-id="90796-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="90796-119">Použití [icordebugregisterset2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) rozhraní na platformách, například IA-64, které vyžadují další registry.</span><span class="sxs-lookup"><span data-stu-id="90796-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90796-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="90796-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90796-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90796-121">Requirements</span></span>  
 <span data-ttu-id="90796-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90796-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90796-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90796-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90796-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90796-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90796-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90796-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90796-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90796-126">See also</span></span>

- [<span data-ttu-id="90796-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="90796-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="90796-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90796-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
