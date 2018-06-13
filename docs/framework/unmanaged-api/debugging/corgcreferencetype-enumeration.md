---
title: CorGCReferenceType – výčet
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 822425b958422ba364a1f10903c7c312ba43fab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408603"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="42c98-102">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="42c98-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="42c98-103">Určuje zdroj objekt tak, aby se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="42c98-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c98-104">Syntax</span></span>  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="42c98-105">Členové</span><span class="sxs-lookup"><span data-stu-id="42c98-105">Members</span></span>  
  
|<span data-ttu-id="42c98-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="42c98-106">Member name</span></span>|<span data-ttu-id="42c98-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42c98-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="42c98-108">Popisovač pro silné odkaz z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="42c98-109">Popisovač pro definovaného silné odkaz z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="42c98-110">Popisovač pro slabé odkazy z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="42c98-111">Popisovač pro slabé počítá odkaz na objekt z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="42c98-112">Popisovač pro objekt počítá odkaz z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="42c98-113">Popisovač pro závislý objekt z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="42c98-114">Asynchronní objekt definovaného v tabulce popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="42c98-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="42c98-115">Silné obslužná rutina, která zachová Přibližná velikost souhrnný uzavření všechny objekty a kořeny objektu v době kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="42c98-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="42c98-116">Odkaz ze spravovaných zásobníku.</span><span class="sxs-lookup"><span data-stu-id="42c98-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="42c98-117">Odkaz z fronty finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="42c98-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="42c98-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="42c98-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="42c98-119">Vrátí pouze silné odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="42c98-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="42c98-120">Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.</span><span class="sxs-lookup"><span data-stu-id="42c98-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="42c98-121">Vrátí jenom slabé odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="42c98-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="42c98-122">Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.</span><span class="sxs-lookup"><span data-stu-id="42c98-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="42c98-123">Vrátí všechny odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="42c98-123">Return all references from the handle table.</span></span> <span data-ttu-id="42c98-124">Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.</span><span class="sxs-lookup"><span data-stu-id="42c98-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42c98-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42c98-125">Remarks</span></span>  
 <span data-ttu-id="42c98-126">`CorGCReferenceType` Výčet je používán následovně:</span><span class="sxs-lookup"><span data-stu-id="42c98-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="42c98-127">Jako hodnotu `type` pole z [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktura, znamená to zdroj odkaz nebo popisovač.</span><span class="sxs-lookup"><span data-stu-id="42c98-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="42c98-128">Jako `types` argument [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metoda, určuje typy obslužných rutin, které chcete zahrnout do výčtu.</span><span class="sxs-lookup"><span data-stu-id="42c98-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c98-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42c98-129">Requirements</span></span>  
 <span data-ttu-id="42c98-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c98-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c98-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42c98-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42c98-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42c98-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42c98-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c98-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c98-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="42c98-134">See Also</span></span>  
 [<span data-ttu-id="42c98-135">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="42c98-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
