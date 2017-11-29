---
title: "ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="05092-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="05092-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="05092-103">Získá enumerátor do zásobníku volání vložených v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="05092-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05092-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05092-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05092-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05092-105">Parameters</span></span>  
 <span data-ttu-id="05092-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="05092-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="05092-107">[out] Ukazatel na adresu [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) rozhraní objekt, který je enumerátor trasování zásobníku pro objekt spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="05092-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05092-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05092-108">Remarks</span></span>  
 <span data-ttu-id="05092-109">Pokud je k dispozici žádné informace zásobníku volání, vrátí metoda `S_OK`, a [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) je platný enumerátor s délkou 0.</span><span class="sxs-lookup"><span data-stu-id="05092-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="05092-110">Pokud je metoda nelze načíst informace trasování zásobníku, je vrácenou hodnotu `E_FAIL` a je vrácena žádná enumerátor.</span><span class="sxs-lookup"><span data-stu-id="05092-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="05092-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objektu je zodpovědná za dekódování dat trasování zásobníku z `_stackTrace` pole objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="05092-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05092-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05092-112">Requirements</span></span>  
 <span data-ttu-id="05092-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05092-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05092-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05092-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05092-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05092-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05092-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05092-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05092-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="05092-117">See Also</span></span>  
 [<span data-ttu-id="05092-118">ICorDebugExceptionObjectValue – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="05092-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="05092-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="05092-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
