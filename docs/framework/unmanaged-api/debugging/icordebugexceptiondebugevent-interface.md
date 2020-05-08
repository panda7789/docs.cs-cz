---
title: Rozhraní ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: dfa65aa1b63c996068e75ff1165111d5fcfe77eb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976002"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="e3243-102">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e3243-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="e3243-103">Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí výjimek.</span><span class="sxs-lookup"><span data-stu-id="e3243-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3243-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e3243-104">Methods</span></span>  
  
|<span data-ttu-id="e3243-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e3243-105">Method</span></span>|<span data-ttu-id="e3243-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e3243-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3243-107">GetFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e3243-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="e3243-108">Získá příznak, který označuje, zda lze výjimku zachytit.</span><span class="sxs-lookup"><span data-stu-id="e3243-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="e3243-109">GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="e3243-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="e3243-110">Získá ukazatel nativního rozhraní pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3243-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="e3243-111">GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="e3243-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="e3243-112">Získá ukazatel zásobníku pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3243-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3243-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3243-113">Remarks</span></span>  
 <span data-ttu-id="e3243-114">`ICorDebugExceptionDebugEvent` Rozhraní je implementováno následujícími typy událostí:</span><span class="sxs-lookup"><span data-stu-id="e3243-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="e3243-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e3243-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e3243-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="e3243-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e3243-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="e3243-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="e3243-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="e3243-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="e3243-119">Rozhraní je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e3243-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="e3243-120">Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e3243-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3243-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3243-121">Requirements</span></span>  
 <span data-ttu-id="e3243-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3243-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3243-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3243-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3243-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3243-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3243-125">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3243-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3243-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3243-126">See also</span></span>

- [<span data-ttu-id="e3243-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3243-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e3243-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="e3243-128">Debugging</span></span>](index.md)
