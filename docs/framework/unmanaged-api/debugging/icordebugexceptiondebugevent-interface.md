---
title: Rozhraní ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522bccb4a424da620063995d02ae15d09ecbf2fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929876"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="e0b40-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e0b40-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="e0b40-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) pro podporu událostí výjimek.</span><span class="sxs-lookup"><span data-stu-id="e0b40-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0b40-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e0b40-104">Methods</span></span>  
  
|<span data-ttu-id="e0b40-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e0b40-105">Method</span></span>|<span data-ttu-id="e0b40-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e0b40-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0b40-107">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b40-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="e0b40-108">Získá příznak, který označuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="e0b40-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="e0b40-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b40-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="e0b40-110">Získá ukazatel nativního rozhraní pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="e0b40-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="e0b40-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="e0b40-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="e0b40-112">Získá ukazatel zásobníku pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="e0b40-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0b40-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0b40-113">Remarks</span></span>  
 <span data-ttu-id="e0b40-114">`ICorDebugExceptionDebugEvent` Rozhraní je implementováno následujícími typy událostí:</span><span class="sxs-lookup"><span data-stu-id="e0b40-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="e0b40-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e0b40-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e0b40-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e0b40-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e0b40-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="e0b40-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e0b40-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="e0b40-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="e0b40-119">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e0b40-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="e0b40-120">Pokus o volání metody `QueryInterface` načtení `E_NOINTERFACE` ukazatele rozhraní pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e0b40-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0b40-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0b40-121">Requirements</span></span>  
 <span data-ttu-id="e0b40-122">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0b40-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0b40-123">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0b40-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0b40-124">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0b40-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0b40-125">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0b40-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0b40-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0b40-126">See also</span></span>

- [<span data-ttu-id="e0b40-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e0b40-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e0b40-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="e0b40-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
