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
ms.openlocfilehash: 38de810509f15cf93475eb000837892b99684fc9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782748"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="81c58-102">ICorDebugExceptionObjectCallStackEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="81c58-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="81c58-103">Získá zadaný počet instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které obsahují informace z zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="81c58-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81c58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81c58-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81c58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81c58-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="81c58-106">pro Počet instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="81c58-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="81c58-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="81c58-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="81c58-108">mimo Ukazatel na počet skutečně vrácených instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="81c58-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81c58-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81c58-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c58-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81c58-110">Requirements</span></span>  
 <span data-ttu-id="81c58-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81c58-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c58-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81c58-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81c58-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81c58-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81c58-114">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c58-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c58-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81c58-115">See also</span></span>

- [<span data-ttu-id="81c58-116">ICorDebugExceptionObjectCallStackEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81c58-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="81c58-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="81c58-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
