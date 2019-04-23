---
title: ICorDebugExceptionObjectCallStackEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c33f76b5eaa87c0b69497547732564921f662d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099466"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="522f9-102">ICorDebugExceptionObjectCallStackEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="522f9-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="522f9-103">Získá zadaný počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instancí, které obsahují informace ze zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="522f9-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="522f9-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="522f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="522f9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="522f9-106">[in] Počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="522f9-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="522f9-107">[out] Pole ukazatelů, každý z nich odkazuje [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="522f9-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="522f9-108">[out] Ukazatel na počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="522f9-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="522f9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="522f9-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="522f9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="522f9-110">Requirements</span></span>  
 <span data-ttu-id="522f9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="522f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="522f9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="522f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="522f9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="522f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="522f9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="522f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522f9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="522f9-115">See also</span></span>

- [<span data-ttu-id="522f9-116">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="522f9-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="522f9-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="522f9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
