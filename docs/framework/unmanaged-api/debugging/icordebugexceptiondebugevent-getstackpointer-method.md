---
title: ICorDebugExceptionDebugEvent::GetStackPointer – metoda
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89802de31ed6db4ef6532a2b4a90a82c4e9a5c72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590848"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="07adf-102">ICorDebugExceptionDebugEvent::GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="07adf-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="07adf-103">Získá ukazatel zásobníku pro události ladění této výjimky.</span><span class="sxs-lookup"><span data-stu-id="07adf-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07adf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07adf-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07adf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07adf-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="07adf-106">[out] Ukazatel na adresu ukazatel zásobníku pro tuto výjimku ladit události.</span><span class="sxs-lookup"><span data-stu-id="07adf-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="07adf-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="07adf-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07adf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07adf-108">Remarks</span></span>  
 <span data-ttu-id="07adf-109">Význam tento ukazatel zásobníku závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="07adf-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="07adf-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="07adf-110">Event type</span></span>|<span data-ttu-id="07adf-111">Význam `pStackPointer` hodnota</span><span class="sxs-lookup"><span data-stu-id="07adf-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="07adf-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="07adf-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="07adf-113">Ukazatel zásobníku rámce, který vyvolal výjimku.</span><span class="sxs-lookup"><span data-stu-id="07adf-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="07adf-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="07adf-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="07adf-115">Ukazatel zásobníku pro kód uživatele rámec co nejblíž koncovým bodem vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="07adf-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="07adf-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="07adf-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="07adf-117">Ukazatel zásobníku rámce, který obsahuje obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="07adf-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="07adf-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="07adf-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="07adf-119">`pStackPointer` je **null**.</span><span class="sxs-lookup"><span data-stu-id="07adf-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="07adf-120">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="07adf-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="07adf-121">Typ události je k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="07adf-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07adf-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07adf-122">Requirements</span></span>  
 <span data-ttu-id="07adf-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07adf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07adf-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07adf-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07adf-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07adf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07adf-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07adf-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07adf-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07adf-127">See also</span></span>
- [<span data-ttu-id="07adf-128">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="07adf-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="07adf-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="07adf-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
