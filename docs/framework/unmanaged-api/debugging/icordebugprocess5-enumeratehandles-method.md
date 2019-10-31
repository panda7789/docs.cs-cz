---
title: ICorDebugProcess5::EnumerateHandles – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129679"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="4dbe8-102">ICorDebugProcess5::EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="4dbe8-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="4dbe8-103">Získá enumerátor pro popisovače objektů v procesu.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dbe8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dbe8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dbe8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dbe8-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="4dbe8-106">pro Bitová kombinace hodnot [CorGCReferenceType –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) , která určuje typ popisovačů, které mají být zahrnuty do kolekce.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="4dbe8-107">mimo Ukazatel na adresu [ICorDebugGCReferenceEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , která je enumerátorem pro objekty, které mají být shromážděny z paměti.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dbe8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4dbe8-108">Remarks</span></span>  
 <span data-ttu-id="4dbe8-109">`EnumerateHandles` je pomocná funkce, která podporuje kontrolu tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="4dbe8-110">Je podobný jako metoda [ICorDebugProcess5:: EnumerateGCReferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) , s výjimkou toho, že místo naplnění kolekce [ICorDebugGCReferenceEnum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) se všemi objekty, které mají být sbírány do paměti, zahrnují pouze objekty, které mají popisovače. Tabulka popisovačů.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="4dbe8-111">Parametr `types` určuje typy popisovačů, které se mají zahrnout do kolekce.</span><span class="sxs-lookup"><span data-stu-id="4dbe8-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="4dbe8-112">`types` může být kterýkoli z následujících tří členů výčtu [CorGCReferenceType –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="4dbe8-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="4dbe8-113">`CorHandleStrongOnly` (zpracovává pouze silné odkazy).</span><span class="sxs-lookup"><span data-stu-id="4dbe8-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="4dbe8-114">`CorHandleWeakOnly` (zpracovává pouze slabé odkazy).</span><span class="sxs-lookup"><span data-stu-id="4dbe8-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="4dbe8-115">`CorHandleAll` (všechny popisovače).</span><span class="sxs-lookup"><span data-stu-id="4dbe8-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dbe8-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4dbe8-116">Requirements</span></span>  
 <span data-ttu-id="4dbe8-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dbe8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dbe8-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4dbe8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dbe8-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4dbe8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dbe8-120">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dbe8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dbe8-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4dbe8-121">See also</span></span>

- [<span data-ttu-id="4dbe8-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="4dbe8-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4dbe8-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="4dbe8-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
