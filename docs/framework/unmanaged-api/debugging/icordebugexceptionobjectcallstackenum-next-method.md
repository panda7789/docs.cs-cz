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
ms.openlocfilehash: 2216ad54c37bcaf62f3ddca6a4d48ef2cb4faf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417424"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="62161-102">ICorDebugExceptionObjectCallStackEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="62161-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="62161-103">Získá zadaný počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instancí, které obsahují informace ze zásobníku volání objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="62161-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62161-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62161-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62161-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62161-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="62161-106">[v] Počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="62161-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="62161-107">[out] Ukazatele, každý z nich odkazuje na pole [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="62161-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="62161-108">[out] Ukazatel na počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="62161-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62161-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62161-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62161-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62161-110">Requirements</span></span>  
 <span data-ttu-id="62161-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62161-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62161-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62161-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62161-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62161-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62161-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62161-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62161-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="62161-115">See Also</span></span>  
 [<span data-ttu-id="62161-116">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62161-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 [<span data-ttu-id="62161-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="62161-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
