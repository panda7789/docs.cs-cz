---
title: ICorDebugExceptionDebugEvent::GetStackPointer – metoda
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b30fae0e0a6b6cca64581ecafe78621c8f0068b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754305"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="86045-102">ICorDebugExceptionDebugEvent::GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="86045-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="86045-103">Získá ukazatel zásobníku pro události ladění této výjimky.</span><span class="sxs-lookup"><span data-stu-id="86045-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86045-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86045-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86045-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86045-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="86045-106">[out] Ukazatel na adresu ukazatel zásobníku pro tuto výjimku ladit události.</span><span class="sxs-lookup"><span data-stu-id="86045-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="86045-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="86045-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86045-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86045-108">Remarks</span></span>  
 <span data-ttu-id="86045-109">Význam tento ukazatel zásobníku závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="86045-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="86045-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="86045-110">Event type</span></span>|<span data-ttu-id="86045-111">Význam `pStackPointer` hodnota</span><span class="sxs-lookup"><span data-stu-id="86045-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="86045-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="86045-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="86045-113">Ukazatel zásobníku rámce, který vyvolal výjimku.</span><span class="sxs-lookup"><span data-stu-id="86045-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="86045-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="86045-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="86045-115">Ukazatel zásobníku pro kód uživatele rámec co nejblíž koncovým bodem vyvolané výjimky.</span><span class="sxs-lookup"><span data-stu-id="86045-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="86045-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="86045-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="86045-117">Ukazatel zásobníku rámce, který obsahuje obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="86045-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="86045-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="86045-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="86045-119">`pStackPointer` je **null**.</span><span class="sxs-lookup"><span data-stu-id="86045-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="86045-120">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="86045-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="86045-121">Typ události je k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="86045-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86045-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86045-122">Requirements</span></span>  
 <span data-ttu-id="86045-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86045-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86045-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86045-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86045-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86045-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86045-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86045-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86045-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86045-127">See also</span></span>

- [<span data-ttu-id="86045-128">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86045-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="86045-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="86045-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
