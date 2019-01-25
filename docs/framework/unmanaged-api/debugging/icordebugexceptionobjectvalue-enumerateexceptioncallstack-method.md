---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028787ef0b93811f42f6c5b28e10665ea12aa334
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727843"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="4ff5f-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="4ff5f-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="4ff5f-103">Získá enumerátor pro zásobník volání, které jsou součástí objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ff5f-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ff5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ff5f-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ff5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ff5f-105">Parameters</span></span>  
 <span data-ttu-id="4ff5f-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="4ff5f-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="4ff5f-107">[out] Ukazatel na adresu [icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) rozhraní objektu, který je výčet trasování zásobníku objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ff5f-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ff5f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ff5f-108">Remarks</span></span>  
 <span data-ttu-id="4ff5f-109">Pokud je k dispozici žádné informace o zásobníku volání, metoda vrátí `S_OK`, a [icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) je platným enumerátorem o délce 0.</span><span class="sxs-lookup"><span data-stu-id="4ff5f-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="4ff5f-110">Pokud je metoda nelze načíst informace o trasování zásobníku, vrácená hodnota je `E_FAIL` a je vrácena žádná enumerátor.</span><span class="sxs-lookup"><span data-stu-id="4ff5f-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="4ff5f-111">[Icordebugexceptionobjectcallstackenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) je zodpovědná za dekódování dat trasování zásobníku z objektu `_stackTrace` pole objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="4ff5f-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ff5f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ff5f-112">Requirements</span></span>  
 <span data-ttu-id="4ff5f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ff5f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ff5f-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ff5f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ff5f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ff5f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ff5f-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ff5f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff5f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ff5f-117">See also</span></span>
- [<span data-ttu-id="4ff5f-118">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ff5f-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="4ff5f-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4ff5f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
