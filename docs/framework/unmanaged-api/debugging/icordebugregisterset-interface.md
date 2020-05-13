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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378274"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="85763-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85763-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="85763-103">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="85763-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85763-104">Metody</span><span class="sxs-lookup"><span data-stu-id="85763-104">Methods</span></span>  
  
|<span data-ttu-id="85763-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="85763-105">Method</span></span>|<span data-ttu-id="85763-106">Popis</span><span class="sxs-lookup"><span data-stu-id="85763-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85763-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="85763-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="85763-108">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="85763-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="85763-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="85763-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="85763-110">Načte bitovou masku, která označuje, které Registry v této `ICorDebugRegisterSet` době jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="85763-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="85763-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="85763-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="85763-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="85763-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="85763-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="85763-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="85763-114">Není implementováno pro .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="85763-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="85763-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="85763-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="85763-116">Není implementováno pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="85763-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85763-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85763-117">Remarks</span></span>  
 <span data-ttu-id="85763-118">`ICorDebugRegisterSet`Rozhraní podporuje pouze 32 bitové Registry.</span><span class="sxs-lookup"><span data-stu-id="85763-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="85763-119">Použijte rozhraní [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.</span><span class="sxs-lookup"><span data-stu-id="85763-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85763-120">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="85763-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85763-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85763-121">Requirements</span></span>  
 <span data-ttu-id="85763-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85763-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85763-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85763-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85763-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85763-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85763-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85763-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85763-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="85763-126">See also</span></span>

- [<span data-ttu-id="85763-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85763-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="85763-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85763-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
