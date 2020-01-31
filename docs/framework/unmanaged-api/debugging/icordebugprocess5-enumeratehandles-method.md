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
ms.openlocfilehash: 2a1653055a3834ce1bed0e7de7877b255bea0c38
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792433"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="0e9a9-102">ICorDebugProcess5::EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="0e9a9-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="0e9a9-103">Získá enumerátor pro popisovače objektů v procesu.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e9a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e9a9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e9a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e9a9-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="0e9a9-106">pro Bitová kombinace hodnot [CorGCReferenceType –](corgcreferencetype-enumeration.md) , která určuje typ popisovačů, které mají být zahrnuty do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-106">[in] A bitwise combination of [CorGCReferenceType](corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="0e9a9-107">mimo Ukazatel na adresu [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md) , která je enumerátorem pro objekty, které mají být shromážděny z paměti.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e9a9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e9a9-108">Remarks</span></span>  
 <span data-ttu-id="0e9a9-109">`EnumerateHandles` je pomocná funkce, která podporuje kontrolu tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="0e9a9-110">Je podobný jako metoda [ICorDebugProcess5:: EnumerateGCReferences –](icordebugprocess5-enumerategcreferences-method.md) , s výjimkou toho, že místo naplnění kolekce [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md) se všemi objekty, které mají být sbírány do paměti, zahrnuje pouze objekty, které mají popisovače z tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="0e9a9-111">Parametr `types` určuje typy popisovačů, které se mají zahrnout do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0e9a9-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="0e9a9-112">`types` může být kterýkoli z následujících tří členů výčtu [CorGCReferenceType –](corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="0e9a9-112">`types` can be any of the following three members of the [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="0e9a9-113">`CorHandleStrongOnly` (zpracovává pouze silné odkazy).</span><span class="sxs-lookup"><span data-stu-id="0e9a9-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="0e9a9-114">`CorHandleWeakOnly` (zpracovává pouze slabé odkazy).</span><span class="sxs-lookup"><span data-stu-id="0e9a9-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="0e9a9-115">`CorHandleAll` (všechny popisovače).</span><span class="sxs-lookup"><span data-stu-id="0e9a9-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e9a9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e9a9-116">Requirements</span></span>  
 <span data-ttu-id="0e9a9-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e9a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e9a9-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0e9a9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e9a9-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e9a9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e9a9-120">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e9a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9a9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e9a9-121">See also</span></span>

- [<span data-ttu-id="0e9a9-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="0e9a9-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0e9a9-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="0e9a9-123">Debugging</span></span>](index.md)
