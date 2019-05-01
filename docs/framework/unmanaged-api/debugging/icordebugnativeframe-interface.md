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
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994614"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="b57f2-102">ICorDebugNativeFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b57f2-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="b57f2-103">Specializovaná implementace ICorDebugFrame pro nativní snímky.</span><span class="sxs-lookup"><span data-stu-id="b57f2-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b57f2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b57f2-104">Methods</span></span>  
  
|<span data-ttu-id="b57f2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-105">Method</span></span>|<span data-ttu-id="b57f2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b57f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b57f2-107">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="b57f2-108">Získá hodnotu, která určuje, jestli je bezpečný pro nastavení ukazatele na instrukci do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="b57f2-109">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="b57f2-110">Získá odsazení rámce zásobníku do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="b57f2-111">GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="b57f2-112">Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo lokální proměnné uloženy ve dvou paměti registrů, které je nativní rámec.</span><span class="sxs-lookup"><span data-stu-id="b57f2-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="b57f2-113">GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="b57f2-114">Získá ukazatel `ICorDebugValue` , který představuje hodnotu místní proměnné, které s nízkou bity jsou uloženy do zadaného registru a vysokou bity jsou uloženy na adrese zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="b57f2-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="b57f2-115">GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="b57f2-116">Získá ukazatel `ICorDebugValue` , který představuje hodnotu lokální proměnné uloženy na adrese zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="b57f2-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="b57f2-117">GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="b57f2-118">Získá ukazatel `ICorDebugValue` , která představuje hodnotu místní proměnné, které vysokou bity jsou uloženy do zadaného registru a nízkou bity jsou uloženy na adrese zadaná paměťová</span><span class="sxs-lookup"><span data-stu-id="b57f2-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="b57f2-119">GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="b57f2-120">Získá ukazatel `ICorDebugValue` , který představuje hodnotu argument nebo lokální proměnné uloženy v zadané nativní registru.</span><span class="sxs-lookup"><span data-stu-id="b57f2-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="b57f2-121">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="b57f2-122">Získá ukazatel [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , která představuje do registru, nastavte pro tento `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="b57f2-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="b57f2-123">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="b57f2-124">Nastaví ukazatele na instrukci do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b57f2-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b57f2-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b57f2-126">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b57f2-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b57f2-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b57f2-127">Requirements</span></span>  
 <span data-ttu-id="b57f2-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b57f2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b57f2-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b57f2-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b57f2-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b57f2-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b57f2-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b57f2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b57f2-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b57f2-132">See also</span></span>

- [<span data-ttu-id="b57f2-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b57f2-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
