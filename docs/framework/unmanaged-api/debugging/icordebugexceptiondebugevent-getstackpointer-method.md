---
title: ICorDebugExceptionDebugEvent::GetStackPointer – metoda
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e724b3a928a23bb44c3d1005024f803b5974e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415552"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="305fb-102">ICorDebugExceptionDebugEvent::GetStackPointer – metoda</span><span class="sxs-lookup"><span data-stu-id="305fb-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="305fb-103">Získá ukazatel zásobníku pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="305fb-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="305fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="305fb-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="305fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="305fb-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="305fb-106">[out] Ukazatel na adresu ukazatel zásobníku pro výjimku ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="305fb-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="305fb-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="305fb-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="305fb-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="305fb-108">Remarks</span></span>  
 <span data-ttu-id="305fb-109">Význam tento ukazatel zásobníku závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="305fb-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="305fb-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="305fb-110">Event type</span></span>|<span data-ttu-id="305fb-111">Význam `pStackPointer` hodnota</span><span class="sxs-lookup"><span data-stu-id="305fb-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="305fb-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="305fb-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="305fb-113">Ukazatel zásobníku pro rámečku, která vrátila výjimku.</span><span class="sxs-lookup"><span data-stu-id="305fb-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="305fb-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="305fb-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="305fb-115">Ukazatel zásobníku pro na uživatelském kódu rámce nejbližší bod vyvolaná výjimka.</span><span class="sxs-lookup"><span data-stu-id="305fb-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="305fb-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="305fb-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="305fb-117">Ukazatel zásobníku pro rámce, který obsahuje obslužná rutina catch.</span><span class="sxs-lookup"><span data-stu-id="305fb-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="305fb-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="305fb-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="305fb-119">`pStackPointer` je **null**.</span><span class="sxs-lookup"><span data-stu-id="305fb-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="305fb-120">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="305fb-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="305fb-121">Typ události má k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="305fb-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="305fb-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="305fb-122">Requirements</span></span>  
 <span data-ttu-id="305fb-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="305fb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="305fb-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="305fb-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="305fb-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="305fb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="305fb-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="305fb-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305fb-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="305fb-127">See Also</span></span>  
 [<span data-ttu-id="305fb-128">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="305fb-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="305fb-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="305fb-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
