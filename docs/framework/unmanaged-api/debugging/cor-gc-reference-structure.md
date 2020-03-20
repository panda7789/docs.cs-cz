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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179319"
---
# <a name="cor_gc_reference-structure"></a><span data-ttu-id="03e02-102">COR_GC_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="03e02-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="03e02-103">Obsahuje informace o objektu, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="03e02-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03e02-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="03e02-105">Členové</span><span class="sxs-lookup"><span data-stu-id="03e02-105">Members</span></span>  
  
|<span data-ttu-id="03e02-106">Člen</span><span class="sxs-lookup"><span data-stu-id="03e02-106">Member</span></span>|<span data-ttu-id="03e02-107">Popis</span><span class="sxs-lookup"><span data-stu-id="03e02-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="03e02-108">Ukazatel na doménu aplikace, do které patří popisovač nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="03e02-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="03e02-109">Jeho hodnota `null`může být .</span><span class="sxs-lookup"><span data-stu-id="03e02-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="03e02-110">Buď ICorDebugValue nebo ICorDebugReferenceValue rozhraní, které odpovídá objektu, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="03e02-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="03e02-111">Hodnota výčtu [CorGCReferenceType,](corgcreferencetype-enumeration.md) která označuje, odkud kořen pochází.</span><span class="sxs-lookup"><span data-stu-id="03e02-111">A [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="03e02-112">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="03e02-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="03e02-113">Další data o objektu, který má být uvolněno.</span><span class="sxs-lookup"><span data-stu-id="03e02-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="03e02-114">Tyto informace závisí na zdroji objektu, jak `type` je uvedeno v poli.</span><span class="sxs-lookup"><span data-stu-id="03e02-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="03e02-115">Další informace naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="03e02-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03e02-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03e02-116">Remarks</span></span>  
 <span data-ttu-id="03e02-117">Pole `type` je hodnota výčtu [CorGCReferenceType,](corgcreferencetype-enumeration.md) která označuje, odkud odkaz pochází.</span><span class="sxs-lookup"><span data-stu-id="03e02-117">The `type` field is a [CorGCReferenceType](corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="03e02-118">Určitá `COR_GC_REFERENCE` hodnota může odrážet některý z následujících druhů spravovaných objektů:</span><span class="sxs-lookup"><span data-stu-id="03e02-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="03e02-119">Objekty ze všech`CorGCReferenceType.CorReferenceStack`spravovaných hromádek ( ).</span><span class="sxs-lookup"><span data-stu-id="03e02-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="03e02-120">To zahrnuje živé odkazy ve spravovaném kódu, stejně jako objekty vytvořené běžným jazykem runtime.</span><span class="sxs-lookup"><span data-stu-id="03e02-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="03e02-121">Objekty z tabulky`CorGCReferenceType.CorHandle*`úchytu ( ).</span><span class="sxs-lookup"><span data-stu-id="03e02-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="03e02-122">To zahrnuje silné`HNDTYPE_STRONG` odkazy `HNDTYPE_REFCOUNT`( a ) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="03e02-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="03e02-123">Objekty z fronty`CorGCReferenceType.CorReferenceFinalizer`finalizační metody ( ).</span><span class="sxs-lookup"><span data-stu-id="03e02-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="03e02-124">Kořeny fronty finalizační metody, dokud není spuštěna finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="03e02-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="03e02-125">Pole `extraData` obsahuje další data v závislosti na zdroji (nebo typu) odkazu.</span><span class="sxs-lookup"><span data-stu-id="03e02-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="03e02-126">Možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="03e02-126">Possible values are:</span></span>  
  
- <span data-ttu-id="03e02-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="03e02-127">`DependentSource`.</span></span> <span data-ttu-id="03e02-128">Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud je `COR_GC_REFERENCE.Location`naživu, kořeny objektu, který má být uvolněna na .</span><span class="sxs-lookup"><span data-stu-id="03e02-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="03e02-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="03e02-129">`RefCount`.</span></span> <span data-ttu-id="03e02-130">Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je referenční počet popisovače.</span><span class="sxs-lookup"><span data-stu-id="03e02-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="03e02-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="03e02-131">`Size`.</span></span> <span data-ttu-id="03e02-132">Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které systém uvolňování paměti vypočítal kořeny objektu.</span><span class="sxs-lookup"><span data-stu-id="03e02-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="03e02-133">Všimněte si, že tento výpočet není nutně aktuální.</span><span class="sxs-lookup"><span data-stu-id="03e02-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e02-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03e02-134">Requirements</span></span>  
 <span data-ttu-id="03e02-135">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e02-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e02-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03e02-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03e02-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03e02-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03e02-138">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e02-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e02-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="03e02-139">See also</span></span>

- [<span data-ttu-id="03e02-140">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="03e02-140">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="03e02-141">ladění</span><span class="sxs-lookup"><span data-stu-id="03e02-141">Debugging</span></span>](index.md)
