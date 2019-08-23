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
ms.openlocfilehash: 6419a525a8a542295751defb97e67a83220730b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965069"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="11bee-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11bee-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="11bee-103">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="11bee-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11bee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="11bee-104">Methods</span></span>  
  
|<span data-ttu-id="11bee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-105">Method</span></span>|<span data-ttu-id="11bee-106">Popis</span><span class="sxs-lookup"><span data-stu-id="11bee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11bee-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="11bee-108">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="11bee-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="11bee-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="11bee-110">Načte bitovou masku, která označuje, které `ICorDebugRegisterSet` Registry v této době jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="11bee-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="11bee-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="11bee-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="11bee-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="11bee-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="11bee-114">Není implementováno pro .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="11bee-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="11bee-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="11bee-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="11bee-116">Není implementováno pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="11bee-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11bee-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11bee-117">Remarks</span></span>  
 <span data-ttu-id="11bee-118">`ICorDebugRegisterSet` Rozhraní podporuje pouze 32 bitové Registry.</span><span class="sxs-lookup"><span data-stu-id="11bee-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="11bee-119">Použijte rozhraní [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.</span><span class="sxs-lookup"><span data-stu-id="11bee-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11bee-120">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="11bee-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11bee-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11bee-121">Requirements</span></span>  
 <span data-ttu-id="11bee-122">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11bee-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11bee-123">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11bee-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11bee-124">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11bee-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11bee-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11bee-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11bee-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11bee-126">See also</span></span>

- [<span data-ttu-id="11bee-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="11bee-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="11bee-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11bee-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
