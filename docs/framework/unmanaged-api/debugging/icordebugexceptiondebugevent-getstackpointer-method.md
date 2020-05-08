---
title: 'ICorDebugExceptionDebugEvent:: GetStackPointer – metoda'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 4f84183dfc23ebc0d0fee9feeb21329c217b9cca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976015"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="58a32-102">ICorDebugExceptionDebugEvent:: GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="58a32-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="58a32-103">Získá ukazatel zásobníku pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="58a32-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58a32-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58a32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58a32-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="58a32-106">mimo Ukazatel na adresu ukazatele zásobníku pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="58a32-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="58a32-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="58a32-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58a32-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58a32-108">Remarks</span></span>  
 <span data-ttu-id="58a32-109">Význam tohoto ukazatele zásobníku závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="58a32-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="58a32-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="58a32-110">Event type</span></span>|<span data-ttu-id="58a32-111">Význam `pStackPointer` hodnoty</span><span class="sxs-lookup"><span data-stu-id="58a32-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="58a32-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="58a32-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="58a32-113">Ukazatel zásobníku pro rámec, který vyvolal výjimku.</span><span class="sxs-lookup"><span data-stu-id="58a32-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="58a32-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="58a32-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="58a32-115">Ukazatel zásobníku pro rámec uživatelského kódu nejblíže k bodu vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="58a32-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="58a32-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="58a32-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="58a32-117">Ukazatel zásobníku pro rámec, který obsahuje obslužnou rutinu catch.</span><span class="sxs-lookup"><span data-stu-id="58a32-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="58a32-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="58a32-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="58a32-119">`pStackPointer`má **hodnotu null**.</span><span class="sxs-lookup"><span data-stu-id="58a32-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="58a32-120">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="58a32-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="58a32-121">Typ události je k dispozici z metody [ICorDebugDebugEvent:: GetEventKind –](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="58a32-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58a32-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58a32-122">Requirements</span></span>  
 <span data-ttu-id="58a32-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58a32-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58a32-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58a32-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58a32-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="58a32-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58a32-126">**Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58a32-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a32-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="58a32-127">See also</span></span>

- [<span data-ttu-id="58a32-128">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="58a32-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="58a32-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58a32-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
