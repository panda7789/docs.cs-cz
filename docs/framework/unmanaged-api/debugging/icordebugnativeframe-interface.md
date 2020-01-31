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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792792"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="adddf-102">ICorDebugNativeFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="adddf-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="adddf-103">Specializovaná implementace ICorDebugFrame používaná pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="adddf-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adddf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="adddf-104">Methods</span></span>  
  
|<span data-ttu-id="adddf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-105">Method</span></span>|<span data-ttu-id="adddf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="adddf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adddf-107">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="adddf-108">Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="adddf-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="adddf-109">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="adddf-110">Získá posun rámce zásobníku do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="adddf-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="adddf-111">GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="adddf-112">Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené ve dvou registrech paměti nativního rámce.</span><span class="sxs-lookup"><span data-stu-id="adddf-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="adddf-113">GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="adddf-114">Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy nízké bity a vysoké bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="adddf-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="adddf-115">GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="adddf-116">Získá ukazatel na `ICorDebugValue`, která představuje hodnotu místní proměnné uložené v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="adddf-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="adddf-117">GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="adddf-118">Získá ukazatel na `ICorDebugValue`, který představuje hodnotu místní proměnné, jejíž horní bity jsou uloženy v zadaném registru a dolní bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="adddf-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="adddf-119">GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="adddf-120">Získá ukazatel na `ICorDebugValue`, která představuje hodnotu argumentu nebo místní proměnnou uloženou v zadaném nativním registru.</span><span class="sxs-lookup"><span data-stu-id="adddf-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="adddf-121">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="adddf-122">Získá ukazatel na [ICorDebugRegisterSet](icordebugregisterset-interface.md) , který představuje sadu registru pro tento `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="adddf-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="adddf-123">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="adddf-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="adddf-124">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="adddf-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adddf-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adddf-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adddf-126">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="adddf-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adddf-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adddf-127">Requirements</span></span>  
 <span data-ttu-id="adddf-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adddf-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adddf-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="adddf-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adddf-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="adddf-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adddf-131">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adddf-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adddf-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adddf-132">See also</span></span>

- [<span data-ttu-id="adddf-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="adddf-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
