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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3cc158c48e8bb9f833429bbddaa74ed459f1b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108823"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="da61d-102">ICorDebugProcess5::EnumerateHandles – metoda</span><span class="sxs-lookup"><span data-stu-id="da61d-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="da61d-103">Získá enumerátor pro objekt popisovače procesu.</span><span class="sxs-lookup"><span data-stu-id="da61d-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da61d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da61d-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da61d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da61d-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="da61d-106">[in] Bitová kombinace hodnot [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnoty, které určuje typ obslužné rutiny, které chcete zahrnout do kolekce.</span><span class="sxs-lookup"><span data-stu-id="da61d-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="da61d-107">[out] Ukazatel na adresu [icordebuggcreferenceenum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , který je enumerátor pro objekty být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="da61d-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da61d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da61d-108">Remarks</span></span>  
 `EnumerateHandles` <span data-ttu-id="da61d-109">je pomocná funkce, která podporuje kontrolu tabulku.</span><span class="sxs-lookup"><span data-stu-id="da61d-109">is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="da61d-110">Se podobá [icordebugprocess5::enumerategcreferences –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, s výjimkou, že místo naplnění [icordebuggcreferenceenum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekci všech objektů, aby byly uklizeny, ho zahrnuje pouze objekty, které mají obslužné rutiny z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="da61d-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="da61d-111">`types` Parametr určuje typy popisovač chcete zahrnout do kolekce.</span><span class="sxs-lookup"><span data-stu-id="da61d-111">The `types` parameter specifies the handle types to include in the collection.</span></span> `types` <span data-ttu-id="da61d-112">může být kterýkoli z následujících tří členů [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) výčtu:</span><span class="sxs-lookup"><span data-stu-id="da61d-112">can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   `CorHandleStrongOnly` <span data-ttu-id="da61d-113">(popisovače pouze odkazy na silné).</span><span class="sxs-lookup"><span data-stu-id="da61d-113">(handles to strong references only).</span></span>  
  
-   `CorHandleWeakOnly` <span data-ttu-id="da61d-114">(popisovače jenom slabé odkazy).</span><span class="sxs-lookup"><span data-stu-id="da61d-114">(handles to weak references only).</span></span>  
  
-   `CorHandleAll` <span data-ttu-id="da61d-115">(všechny popisovače).</span><span class="sxs-lookup"><span data-stu-id="da61d-115">(all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da61d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da61d-116">Requirements</span></span>  
 <span data-ttu-id="da61d-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da61d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da61d-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da61d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da61d-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da61d-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="da61d-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="da61d-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da61d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da61d-121">See also</span></span>

- [<span data-ttu-id="da61d-122">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="da61d-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="da61d-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="da61d-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
