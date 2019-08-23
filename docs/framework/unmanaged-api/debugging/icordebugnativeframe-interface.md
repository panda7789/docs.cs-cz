---
title: ICorDebugNativeFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912803"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="c5ad3-102">ICorDebugNativeFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5ad3-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="c5ad3-103">Specializovaná implementace ICorDebugFrame používaná pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5ad3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c5ad3-104">Methods</span></span>  
  
|<span data-ttu-id="c5ad3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-105">Method</span></span>|<span data-ttu-id="c5ad3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c5ad3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5ad3-107">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="c5ad3-108">Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="c5ad3-109">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="c5ad3-110">Získá posun rámce zásobníku do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="c5ad3-111">GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="c5ad3-112">Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené ve dvou registrech paměti nativního rámce.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="c5ad3-113">GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="c5ad3-114">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy nízké bity a vysoké bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c5ad3-115">GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="c5ad3-116">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu místní proměnné uložené v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c5ad3-117">GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="c5ad3-118">Získá ukazatel na objekt `ICorDebugValue` , který představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy vysoké bity a dolní bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="c5ad3-119">GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="c5ad3-120">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu argumentu nebo místní proměnnou uloženou v zadaném nativním registru.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="c5ad3-121">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="c5ad3-122">Získá ukazatel na [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , který představuje sadu registru pro tento `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="c5ad3-123">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="c5ad3-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="c5ad3-124">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5ad3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5ad3-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5ad3-126">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c5ad3-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ad3-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5ad3-127">Requirements</span></span>  
 <span data-ttu-id="c5ad3-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5ad3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5ad3-129">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5ad3-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5ad3-130">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5ad3-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5ad3-131">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ad3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ad3-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5ad3-132">See also</span></span>

- [<span data-ttu-id="c5ad3-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c5ad3-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
