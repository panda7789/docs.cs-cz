---
title: Rozhraní ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 168ba2945608a5b26432c5a0f583e5d406f6ce9b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782833"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="14870-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="14870-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="14870-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimek.</span><span class="sxs-lookup"><span data-stu-id="14870-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14870-104">Metody</span><span class="sxs-lookup"><span data-stu-id="14870-104">Methods</span></span>  
  
|<span data-ttu-id="14870-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="14870-105">Method</span></span>|<span data-ttu-id="14870-106">Popis</span><span class="sxs-lookup"><span data-stu-id="14870-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14870-107">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="14870-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="14870-108">Získá příznak, který označuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="14870-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="14870-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="14870-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="14870-110">Získá ukazatel nativního rozhraní pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="14870-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="14870-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="14870-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="14870-112">Získá ukazatel zásobníku pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="14870-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14870-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14870-113">Remarks</span></span>  
 <span data-ttu-id="14870-114">Rozhraní `ICorDebugExceptionDebugEvent` je implementováno následujícími typy událostí:</span><span class="sxs-lookup"><span data-stu-id="14870-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="14870-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="14870-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="14870-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="14870-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="14870-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="14870-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="14870-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="14870-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="14870-119">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14870-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="14870-120">Pokus o volání `QueryInterface` pro načtení ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="14870-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14870-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14870-121">Requirements</span></span>  
 <span data-ttu-id="14870-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14870-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14870-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="14870-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14870-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="14870-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14870-125">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14870-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14870-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14870-126">See also</span></span>

- [<span data-ttu-id="14870-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="14870-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="14870-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="14870-128">Debugging</span></span>](index.md)
