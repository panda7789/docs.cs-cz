---
title: COR_GC_REFERENCE – struktura
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099145"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="35b5f-102">COR_GC_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="35b5f-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="35b5f-103">Obsahuje informace o objektu, který má být shromážděn z paměti.</span><span class="sxs-lookup"><span data-stu-id="35b5f-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35b5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35b5f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="35b5f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="35b5f-105">Members</span></span>  
  
|<span data-ttu-id="35b5f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="35b5f-106">Member</span></span>|<span data-ttu-id="35b5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="35b5f-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="35b5f-108">Ukazatel na doménu aplikace, ke které patří popisovač nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="35b5f-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="35b5f-109">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="35b5f-110">Rozhraní ICorDebugValue nebo ICorDebugReferenceValue, které odpovídá objektu, který má být uvolněn do paměti.</span><span class="sxs-lookup"><span data-stu-id="35b5f-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="35b5f-111">Hodnota výčtu [CorGCReferenceType –](corgcreferencetype-enumeration.md) , která určuje, odkud kořen pochází.</span><span class="sxs-lookup"><span data-stu-id="35b5f-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="35b5f-112">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="35b5f-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="35b5f-113">Další informace o objektu, který má být shromážděn do paměti.</span><span class="sxs-lookup"><span data-stu-id="35b5f-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="35b5f-114">Tyto informace závisí na zdroji objektu, jak je uvedeno v poli `type`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="35b5f-115">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="35b5f-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35b5f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35b5f-116">Remarks</span></span>  
 <span data-ttu-id="35b5f-117">Pole `type` je hodnota výčtu [CorGCReferenceType –](corgcreferencetype-enumeration.md) , která určuje, odkud odkaz pochází.</span><span class="sxs-lookup"><span data-stu-id="35b5f-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="35b5f-118">Konkrétní hodnota `COR_GC_REFERENCE` může odrážet kterýkoli z následujících typů spravovaných objektů:</span><span class="sxs-lookup"><span data-stu-id="35b5f-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="35b5f-119">Objekty ze všech spravovaných zásobníků (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="35b5f-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="35b5f-120">To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="35b5f-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="35b5f-121">Objekty z tabulky Handles (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="35b5f-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="35b5f-122">To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="35b5f-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="35b5f-123">Objekty z fronty finalizační metody (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="35b5f-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="35b5f-124">Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="35b5f-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="35b5f-125">Pole `extraData` obsahuje další data v závislosti na zdroji (nebo typu) odkazu.</span><span class="sxs-lookup"><span data-stu-id="35b5f-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="35b5f-126">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="35b5f-126">Possible values are:</span></span>  
  
- <span data-ttu-id="35b5f-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-127">`DependentSource`.</span></span> <span data-ttu-id="35b5f-128">Pokud je `type` `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud je aktivní, objekt, který má být uvolněn do paměti v `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="35b5f-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-129">`RefCount`.</span></span> <span data-ttu-id="35b5f-130">Pokud je `type` `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů daného popisovače.</span><span class="sxs-lookup"><span data-stu-id="35b5f-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="35b5f-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="35b5f-131">`Size`.</span></span> <span data-ttu-id="35b5f-132">Pokud je `type` `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektu, pro který systém uvolňování paměti vypočítal kořeny objektů.</span><span class="sxs-lookup"><span data-stu-id="35b5f-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="35b5f-133">Všimněte si, že tento výpočet není nutně aktuální.</span><span class="sxs-lookup"><span data-stu-id="35b5f-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35b5f-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35b5f-134">Requirements</span></span>  
 <span data-ttu-id="35b5f-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35b5f-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35b5f-136">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35b5f-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35b5f-137">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35b5f-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35b5f-138">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35b5f-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35b5f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35b5f-139">See also</span></span>

- [<span data-ttu-id="35b5f-140">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="35b5f-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="35b5f-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="35b5f-141">Debugging</span></span>](index.md)
