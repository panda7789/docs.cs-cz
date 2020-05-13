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
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206599"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="cd910-102">ICorDebugNativeFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd910-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="cd910-103">Specializovaná implementace ICorDebugFrame používaná pro nativní rámce.</span><span class="sxs-lookup"><span data-stu-id="cd910-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd910-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd910-104">Methods</span></span>  
  
|<span data-ttu-id="cd910-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-105">Method</span></span>|<span data-ttu-id="cd910-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cd910-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd910-107">CanSetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="cd910-108">Získá hodnotu, která označuje, zda je bezpečné nastavit ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="cd910-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="cd910-109">GetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="cd910-110">Získá posun rámce zásobníku do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="cd910-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="cd910-111">GetLocalDoubleRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="cd910-112">Získá ukazatel na ICorDebugValue, který představuje hodnotu argumentu nebo místní proměnné uložené ve dvou registrech paměti nativního rámce.</span><span class="sxs-lookup"><span data-stu-id="cd910-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="cd910-113">GetLocalMemoryRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="cd910-114">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy nízké bity a vysoké bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="cd910-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="cd910-115">GetLocalMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="cd910-116">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu místní proměnné uložené v zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="cd910-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="cd910-117">GetLocalRegisterMemoryValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="cd910-118">Získá ukazatel na objekt `ICorDebugValue` , který představuje hodnotu místní proměnné, z níž jsou v zadaném registru uloženy vysoké bity a dolní bity jsou uloženy na zadané adrese paměti.</span><span class="sxs-lookup"><span data-stu-id="cd910-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="cd910-119">GetLocalRegisterValue – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="cd910-120">Získá ukazatel na `ICorDebugValue` , který představuje hodnotu argumentu nebo místní proměnnou uloženou v zadaném nativním registru.</span><span class="sxs-lookup"><span data-stu-id="cd910-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="cd910-121">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="cd910-122">Získá ukazatel na [ICorDebugRegisterSet](icordebugregisterset-interface.md) , který představuje sadu registru pro tento `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="cd910-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="cd910-123">SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="cd910-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="cd910-124">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="cd910-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd910-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd910-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd910-126">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="cd910-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd910-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd910-127">Requirements</span></span>  
 <span data-ttu-id="cd910-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd910-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd910-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cd910-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd910-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cd910-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd910-131">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd910-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd910-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd910-132">See also</span></span>

- [<span data-ttu-id="cd910-133">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd910-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
