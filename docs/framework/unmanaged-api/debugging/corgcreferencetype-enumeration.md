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
ms.openlocfilehash: eafae181c74d9f3842f7f0d547bcccbbb28c09e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132125"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="37340-102">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="37340-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="37340-103">Určuje zdroj objektu, který má být shromážděn do paměti.</span><span class="sxs-lookup"><span data-stu-id="37340-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37340-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37340-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="37340-105">Členové</span><span class="sxs-lookup"><span data-stu-id="37340-105">Members</span></span>  
  
|<span data-ttu-id="37340-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="37340-106">Member name</span></span>|<span data-ttu-id="37340-107">Popis</span><span class="sxs-lookup"><span data-stu-id="37340-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="37340-108">Popisovač na silný odkaz z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="37340-109">Popisovač připnutého silného odkazu z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="37340-110">Popisovač na slabý odkaz z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="37340-111">Popisovač slabého objektu s vypočítaným odkazem z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="37340-112">Popisovač objektu počítaného odkazem z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="37340-113">Popisovač závislého objektu z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="37340-114">Asynchronní připnutý objekt z tabulky popisovače objektu.</span><span class="sxs-lookup"><span data-stu-id="37340-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="37340-115">Silný popisovač, který při uvolňování paměti udržuje přibližnou velikost souhrnu všech objektů a kořenových objektů.</span><span class="sxs-lookup"><span data-stu-id="37340-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="37340-116">Odkaz ze spravovaného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="37340-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="37340-117">Odkaz z fronty finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="37340-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="37340-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="37340-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="37340-119">Vrátí pouze silné odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="37340-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="37340-120">Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37340-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="37340-121">Vrátí pouze slabé odkazy z tabulky popisovačů.</span><span class="sxs-lookup"><span data-stu-id="37340-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="37340-122">Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37340-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="37340-123">Vrátí všechny odkazy z tabulky popisovače.</span><span class="sxs-lookup"><span data-stu-id="37340-123">Return all references from the handle table.</span></span> <span data-ttu-id="37340-124">Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="37340-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37340-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37340-125">Remarks</span></span>  
 <span data-ttu-id="37340-126">`CorGCReferenceType` výčet se používá následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="37340-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="37340-127">Jako hodnota pole `type` struktury [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) označuje zdroj odkazu nebo popisovače.</span><span class="sxs-lookup"><span data-stu-id="37340-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="37340-128">Jako argument `types` pro metodu [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) určuje typy popisovačů, které mají být zahrnuty do výčtu.</span><span class="sxs-lookup"><span data-stu-id="37340-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37340-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37340-129">Requirements</span></span>  
 <span data-ttu-id="37340-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37340-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37340-131">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37340-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37340-132">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37340-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37340-133">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37340-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37340-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37340-134">See also</span></span>

- [<span data-ttu-id="37340-135">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="37340-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
