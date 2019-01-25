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
ms.openlocfilehash: 54ac36f6d0dba92742ea7a7acfadc194930ccd74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516440"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="12b2b-102">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="12b2b-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="12b2b-103">Identifikuje zdrojový objekt bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="12b2b-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12b2b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="12b2b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="12b2b-105">Members</span></span>  
  
|<span data-ttu-id="12b2b-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="12b2b-106">Member name</span></span>|<span data-ttu-id="12b2b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="12b2b-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="12b2b-108">Popisovač silného odkazu z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="12b2b-109">Popisovač připnuté silného odkazu z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="12b2b-110">Popisovač nestálý odkaz z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="12b2b-111">Popisovač pro objekt slabé počítáním referencí z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="12b2b-112">Popisovač pro objekt počítáním referencí z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="12b2b-113">Popisovač pro závislý objekt z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="12b2b-114">Asynchronní objekt připnuté z tabulky popisovač objektu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="12b2b-115">Silný popisovač, který udržuje přibližné velikosti kolektivní ukončení všech objektů a objektů kořeny během uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="12b2b-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="12b2b-116">Odkaz ze spravované zásobníku.</span><span class="sxs-lookup"><span data-stu-id="12b2b-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="12b2b-117">Odkaz z fronta finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="12b2b-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="12b2b-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="12b2b-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="12b2b-119">Vrátíte pouze silné odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="12b2b-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="12b2b-120">Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.</span><span class="sxs-lookup"><span data-stu-id="12b2b-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="12b2b-121">Vrátí jenom slabé odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="12b2b-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="12b2b-122">Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.</span><span class="sxs-lookup"><span data-stu-id="12b2b-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="12b2b-123">Vrátí všechny odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="12b2b-123">Return all references from the handle table.</span></span> <span data-ttu-id="12b2b-124">Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.</span><span class="sxs-lookup"><span data-stu-id="12b2b-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12b2b-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12b2b-125">Remarks</span></span>  
 <span data-ttu-id="12b2b-126">`CorGCReferenceType` Výčet je používán následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="12b2b-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="12b2b-127">Jako hodnotu `type` pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) strukturu, určuje zdroj odkazu nebo popisovač.</span><span class="sxs-lookup"><span data-stu-id="12b2b-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="12b2b-128">Jako `types` argument [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Určuje typy obslužné rutiny, které chcete zahrnout do výčtu.</span><span class="sxs-lookup"><span data-stu-id="12b2b-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b2b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12b2b-129">Requirements</span></span>  
 <span data-ttu-id="12b2b-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b2b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b2b-131">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12b2b-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12b2b-132">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12b2b-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12b2b-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b2b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b2b-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12b2b-134">See also</span></span>
- [<span data-ttu-id="12b2b-135">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="12b2b-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
