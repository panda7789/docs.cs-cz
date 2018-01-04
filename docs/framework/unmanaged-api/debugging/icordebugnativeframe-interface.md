---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edd49d745be9db0c4c5309cf5febc3ff651a860f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="c4b0e-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="c4b0e-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="c4b0e-103">Specializovaná implementace ICorDebugFrame používá pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4b0e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4b0e-104">Methods</span></span>  
  
|<span data-ttu-id="c4b0e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-105">Method</span></span>|<span data-ttu-id="c4b0e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4b0e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4b0e-107">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="c4b0e-108">Získá hodnotu, která určuje, zda je bezpečné nastavení ukazatel instrukce do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="c4b0e-109">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="c4b0e-110">Získá Posun rámce zásobníku do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="c4b0e-111">GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="c4b0e-112">Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené registry dvě paměti nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="c4b0e-113">GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="c4b0e-114">Získá odkazy `ICorDebugValue` představující hodnotu místní proměnné, které nízkou bity jsou uloženy v zadané registrace a vysokou bity jsou uloženy v zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c4b0e-115">GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="c4b0e-116">Získá ukazatel na `ICorDebugValue` představující hodnotu místní proměnné uložené v zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c4b0e-117">GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="c4b0e-118">Získá odkazy `ICorDebugValue` představující hodnotu místní proměnné, které vysoké bity jsou uloženy v zadané registrace a nízkou bity jsou uloženy v zadané paměti</span><span class="sxs-lookup"><span data-stu-id="c4b0e-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="c4b0e-119">GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="c4b0e-120">Získá odkazy `ICorDebugValue` představující hodnotu argumentu nebo místní proměnné uložené v zadané nativní registrace.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="c4b0e-121">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="c4b0e-122">Získá odkazy [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) představující registrace nastavit pro `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="c4b0e-123">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c4b0e-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="c4b0e-124">Nastaví ukazatel instrukce do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4b0e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4b0e-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4b0e-126">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4b0e-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b0e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4b0e-127">Requirements</span></span>  
 <span data-ttu-id="c4b0e-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b0e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b0e-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b0e-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b0e-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b0e-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b0e-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b0e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b0e-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4b0e-132">See Also</span></span>  
 [<span data-ttu-id="c4b0e-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4b0e-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
