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
ms.openlocfilehash: 6c742f541b358b40e6e2fd44ca437b0dd72e29b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091089"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="41f74-102">ICorDebugExceptionObjectCallStackEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="41f74-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="41f74-103">Získá zadaný počet instancí [CorDebugExceptionObjectStackFrame –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) , které obsahují informace z zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="41f74-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f74-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41f74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41f74-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="41f74-106">pro Počet instancí [CorDebugExceptionObjectStackFrame –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) , které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="41f74-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="41f74-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugExceptionObjectStackFrame –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="41f74-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="41f74-108">mimo Ukazatel na počet skutečně vrácených instancí [CorDebugExceptionObjectStackFrame –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="41f74-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41f74-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41f74-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f74-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41f74-110">Requirements</span></span>  
 <span data-ttu-id="41f74-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41f74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41f74-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41f74-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41f74-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41f74-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41f74-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41f74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f74-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41f74-115">See also</span></span>

- [<span data-ttu-id="41f74-116">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41f74-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="41f74-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="41f74-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
