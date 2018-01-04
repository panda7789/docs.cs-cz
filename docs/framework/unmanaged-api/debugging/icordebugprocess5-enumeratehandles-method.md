---
title: "ICorDebugProcess5::EnumerateHandles – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9bf9f1a4d565e0af4f3ee34a2805116407027d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="d7887-102">ICorDebugProcess5::EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="d7887-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="d7887-103">Získá enumerátor pro objekt popisovače v procesu.</span><span class="sxs-lookup"><span data-stu-id="d7887-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7887-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7887-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7887-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7887-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="d7887-106">[v] Bitovou kombinaci [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnoty, které určuje typ obslužné rutiny, které chcete zahrnout do kolekce.</span><span class="sxs-lookup"><span data-stu-id="d7887-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="d7887-107">[out] Ukazatel na adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) tedy enumerátor pro objekty být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d7887-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7887-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7887-108">Remarks</span></span>  
 <span data-ttu-id="d7887-109">`EnumerateHandles`je pomocné funkce, která podporuje kontroly tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="d7887-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="d7887-110">Je podobná [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metoda, vyjma toho, že místo naplnění [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekce se všemi objekty být uklizeny, ho obsahuje pouze objekty, které mají obslužné rutiny z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="d7887-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="d7887-111">`types` Parametr určuje typy popisovač pro zahrnutí do kolekce.</span><span class="sxs-lookup"><span data-stu-id="d7887-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="d7887-112">`types`může být libovolná z následujících tří členů [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) výčtu:</span><span class="sxs-lookup"><span data-stu-id="d7887-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="d7887-113">`CorHandleStrongOnly`(zpracovává jenom silné odkazů na).</span><span class="sxs-lookup"><span data-stu-id="d7887-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="d7887-114">`CorHandleWeakOnly`(zpracovává jenom slabé odkazy).</span><span class="sxs-lookup"><span data-stu-id="d7887-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="d7887-115">`CorHandleAll`(všechny obslužné rutiny).</span><span class="sxs-lookup"><span data-stu-id="d7887-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7887-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7887-116">Requirements</span></span>  
 <span data-ttu-id="d7887-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7887-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7887-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7887-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7887-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7887-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7887-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7887-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7887-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7887-121">See Also</span></span>  
 [<span data-ttu-id="d7887-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="d7887-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="d7887-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="d7887-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
