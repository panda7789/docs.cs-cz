---
title: ICorDebugExceptionDebugEvent::GetNativeIP – metoda
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0069f301df9908a584608c7d20e5348de47361c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501601"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="b226e-102">ICorDebugExceptionDebugEvent::GetNativeIP – metoda</span><span class="sxs-lookup"><span data-stu-id="b226e-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="b226e-103">Získá ukazatel na nativní instrukce pro tuto událost výjimky ladění.</span><span class="sxs-lookup"><span data-stu-id="b226e-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b226e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b226e-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b226e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b226e-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="b226e-106">[out] Ukazatel na ukazatele na instrukci pro tuto výjimku ladit události.</span><span class="sxs-lookup"><span data-stu-id="b226e-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="b226e-107">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="b226e-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b226e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b226e-108">Remarks</span></span>  
 <span data-ttu-id="b226e-109">Význam tomto ukazateli instrukcí závisí na typu události, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b226e-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="b226e-110">Typ události</span><span class="sxs-lookup"><span data-stu-id="b226e-110">Event type</span></span>|<span data-ttu-id="b226e-111">Význam `pStackPointer` hodnota</span><span class="sxs-lookup"><span data-stu-id="b226e-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="b226e-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="b226e-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="b226e-113">Adresa neškodné instrukce.</span><span class="sxs-lookup"><span data-stu-id="b226e-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="b226e-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="b226e-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="b226e-115">Adresa kódu v rámci indikován [getstackpointer –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody, kde bude provádění pokračovat, pokud měl vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="b226e-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="b226e-116">Výjimka může nebo nemusí způsobit odlišný kód, jako je blok catch `try/catch/finally` klauzuli, který se spustí v tomto snímku.</span><span class="sxs-lookup"><span data-stu-id="b226e-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="b226e-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="b226e-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="b226e-118">Kód adres where `catch` provádění obslužná rutina se spustí v rámci indikován [getstackpointer –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b226e-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="b226e-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="b226e-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="b226e-120">`pIP` je 0.</span><span class="sxs-lookup"><span data-stu-id="b226e-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="b226e-121">Typ události je k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b226e-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b226e-122">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b226e-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b226e-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b226e-123">Requirements</span></span>  
 <span data-ttu-id="b226e-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b226e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b226e-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b226e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b226e-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b226e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b226e-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b226e-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b226e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b226e-128">See also</span></span>
- [<span data-ttu-id="b226e-129">ICorDebugExceptionDebugEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b226e-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="b226e-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b226e-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
