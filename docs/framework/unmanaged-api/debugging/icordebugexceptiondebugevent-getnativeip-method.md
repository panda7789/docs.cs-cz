---
title: "ICorDebugExceptionDebugEvent::GetNativeIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 616f0a9787220aba0cc4d460c80b856076e1e437
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="708ef-102">ICorDebugExceptionDebugEvent::GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="708ef-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="708ef-103">Získá ukazatel na nativní instrukce pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="708ef-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="708ef-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="708ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="708ef-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="708ef-106">[out] Ukazatel na ukazatel instrukce pro tuto výjimku ladění událostí.</span><span class="sxs-lookup"><span data-stu-id="708ef-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="708ef-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="708ef-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="708ef-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="708ef-108">Remarks</span></span>  
 <span data-ttu-id="708ef-109">Význam tento ukazatel instrukce závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="708ef-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="708ef-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="708ef-110">Event type</span></span>|<span data-ttu-id="708ef-111">Význam `pStackPointer` hodnota</span><span class="sxs-lookup"><span data-stu-id="708ef-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="708ef-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="708ef-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="708ef-113">Adresa chybující instrukcí.</span><span class="sxs-lookup"><span data-stu-id="708ef-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="708ef-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="708ef-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="708ef-115">Adresu kódu v rámci indikován [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metoda, kde by provádění obnoveno, pokud měl byla vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="708ef-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="708ef-116">Výjimka může nebo nemusí způsobit jiný kód, jako je blok catch `try/catch/finally` klauzule spouštění této rámce.</span><span class="sxs-lookup"><span data-stu-id="708ef-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="708ef-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="708ef-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="708ef-118">Kód adres kde `catch` provádění obslužná rutina se spustí v rámci indikován [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="708ef-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="708ef-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="708ef-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="708ef-120">`pIP`je 0.</span><span class="sxs-lookup"><span data-stu-id="708ef-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="708ef-121">Typ události má k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="708ef-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="708ef-122">Tato metoda je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="708ef-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708ef-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="708ef-123">Requirements</span></span>  
 <span data-ttu-id="708ef-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="708ef-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708ef-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="708ef-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="708ef-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="708ef-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="708ef-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708ef-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708ef-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="708ef-128">See Also</span></span>  
 [<span data-ttu-id="708ef-129">Rozhraní ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="708ef-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="708ef-130">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="708ef-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
