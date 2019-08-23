---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP – metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa1a160bb316831540f68713647dbdc4b0f6895
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951853"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="0c8f5-102">ICorDebugExceptionDebugEvent:: GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="0c8f5-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="0c8f5-103">Získá nativní ukazatel instrukcí pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c8f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c8f5-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="0c8f5-106">mimo Ukazatel na ukazatel instrukcí pro tuto událost ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="0c8f5-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c8f5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c8f5-108">Remarks</span></span>  
 <span data-ttu-id="0c8f5-109">Význam tohoto ukazatele instrukcí závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0c8f5-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="0c8f5-110">Event type</span></span>|<span data-ttu-id="0c8f5-111">`pStackPointer` Význam hodnoty</span><span class="sxs-lookup"><span data-stu-id="0c8f5-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="0c8f5-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0c8f5-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0c8f5-113">Adresa instrukce pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="0c8f5-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="0c8f5-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0c8f5-115">Adresa kódu v rámci, která je označena metodou [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) , ve které by provádění pokračovalo, pokud nebyla vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="0c8f5-116">Výjimka může nebo nemusí způsobit jiný kód, jako je například blok `try/catch/finally` catch klauzule, která má být provedena v tomto rámci.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="0c8f5-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="0c8f5-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0c8f5-118">Adresa kódu, kde `catch` se spustí spuštění obslužné rutiny v rámci snímku určeného metodou [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0c8f5-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="0c8f5-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="0c8f5-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="0c8f5-120">`pIP`je 0.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="0c8f5-121">Typ události je k dispozici z metody [ICorDebugDebugEvent:: GetEventKind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0c8f5-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c8f5-122">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0c8f5-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8f5-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c8f5-123">Requirements</span></span>  
 <span data-ttu-id="0c8f5-124">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c8f5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8f5-125">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c8f5-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c8f5-126">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c8f5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8f5-127">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8f5-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8f5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c8f5-128">See also</span></span>

- [<span data-ttu-id="0c8f5-129">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c8f5-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="0c8f5-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0c8f5-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
