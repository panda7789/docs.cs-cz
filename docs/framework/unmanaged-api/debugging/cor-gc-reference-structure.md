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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 848765a4ea9657020bd84e476f992ae69750dda9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617689"
---
# <a name="corgcreference-structure"></a><span data-ttu-id="069de-102">COR_GC_REFERENCE – struktura</span><span class="sxs-lookup"><span data-stu-id="069de-102">COR_GC_REFERENCE Structure</span></span>
<span data-ttu-id="069de-103">Obsahuje informace o objektu, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="069de-103">Contains information about an object that is to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="069de-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a><span data-ttu-id="069de-105">Členové</span><span class="sxs-lookup"><span data-stu-id="069de-105">Members</span></span>  
  
|<span data-ttu-id="069de-106">Člen</span><span class="sxs-lookup"><span data-stu-id="069de-106">Member</span></span>|<span data-ttu-id="069de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="069de-107">Description</span></span>|  
|------------|-----------------|  
|`domain`|<span data-ttu-id="069de-108">Ukazatel na doménu aplikace, ke kterému patří popisovač nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="069de-108">A pointer to the application domain to which the handle or object belongs.</span></span> <span data-ttu-id="069de-109">Jeho hodnota může být `null`.</span><span class="sxs-lookup"><span data-stu-id="069de-109">Its value may be `null`.</span></span>|  
|`location`|<span data-ttu-id="069de-110">ICorDebugValue nebo icordebugreferencevalue – rozhraní, která odpovídá objekt, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="069de-110">Either an ICorDebugValue or an ICorDebugReferenceValue interface that corresponds to the object to be garbage-collected.</span></span>|  
|`type`|<span data-ttu-id="069de-111">A [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází kořenový adresář.</span><span class="sxs-lookup"><span data-stu-id="069de-111">A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the root came from.</span></span> <span data-ttu-id="069de-112">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="069de-112">For more information, see the Remarks section.</span></span>|  
|`extraData`|<span data-ttu-id="069de-113">Údaje o objekt, který má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="069de-113">Additional data about the object to be garbage-collected.</span></span> <span data-ttu-id="069de-114">Tyto informace závisí na zdroji objektu, je určeno `type` pole.</span><span class="sxs-lookup"><span data-stu-id="069de-114">This information depends on the source of the object, as indicated by the `type` field.</span></span> <span data-ttu-id="069de-115">Další informace najdete v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="069de-115">For more information, see the Remarks section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="069de-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="069de-116">Remarks</span></span>  
 <span data-ttu-id="069de-117">`type` Je pole [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází odkaz.</span><span class="sxs-lookup"><span data-stu-id="069de-117">The `type` field is a [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration value that indicates where the reference came from.</span></span> <span data-ttu-id="069de-118">Konkrétní `COR_GC_REFERENCE` hodnotu můžete sledovat některé z následujících typů spravovaných objektů:</span><span class="sxs-lookup"><span data-stu-id="069de-118">A particular `COR_GC_REFERENCE` value can reflect any of the following kinds of managed objects:</span></span>  
  
- <span data-ttu-id="069de-119">Objekty z všechny spravované zásobníky (`CorGCReferenceType.CorReferenceStack`).</span><span class="sxs-lookup"><span data-stu-id="069de-119">Objects from all managed stacks (`CorGCReferenceType.CorReferenceStack`).</span></span> <span data-ttu-id="069de-120">To zahrnuje živé odkazy ve spravovaném kódu, jakož i objekty vytvořené modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="069de-120">This includes live references in managed code, as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="069de-121">Objekty z tabulky popisovače (`CorGCReferenceType.CorHandle*`).</span><span class="sxs-lookup"><span data-stu-id="069de-121">Objects from the handle table (`CorGCReferenceType.CorHandle*`).</span></span> <span data-ttu-id="069de-122">Jedná se o silná odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.</span><span class="sxs-lookup"><span data-stu-id="069de-122">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="069de-123">Objekty ve frontě finalizační metody (`CorGCReferenceType.CorReferenceFinalizer`).</span><span class="sxs-lookup"><span data-stu-id="069de-123">Objects from the finalizer queue (`CorGCReferenceType.CorReferenceFinalizer`).</span></span> <span data-ttu-id="069de-124">Fronta finalizační metody kořeny objekty, dokud finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="069de-124">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
 <span data-ttu-id="069de-125">`extraData` Pole obsahuje doplňující data v závislosti na zdroj (nebo typ) odkaz.</span><span class="sxs-lookup"><span data-stu-id="069de-125">The `extraData` field contains extra data depending on the source (or type) of the reference.</span></span> <span data-ttu-id="069de-126">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="069de-126">Possible values are:</span></span>  
  
- <span data-ttu-id="069de-127">`DependentSource`.</span><span class="sxs-lookup"><span data-stu-id="069de-127">`DependentSource`.</span></span> <span data-ttu-id="069de-128">Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud zachování připojení, kořenových adresářů objekt, který má být prováděno uvolnění paměti na `COR_GC_REFERENCE.Location`.</span><span class="sxs-lookup"><span data-stu-id="069de-128">If the `type` is `CorGCREferenceType.CorHandleStrongDependent`, this field is the object that, if alive, roots the object to be garbage-collected at `COR_GC_REFERENCE.Location`.</span></span>  
  
- <span data-ttu-id="069de-129">`RefCount`.</span><span class="sxs-lookup"><span data-stu-id="069de-129">`RefCount`.</span></span> <span data-ttu-id="069de-130">Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů popisovače.</span><span class="sxs-lookup"><span data-stu-id="069de-130">If the `type` is `CorGCREferenceType.CorHandleStrongRefCount`, this field is the reference count of the handle.</span></span>  
  
- <span data-ttu-id="069de-131">`Size`.</span><span class="sxs-lookup"><span data-stu-id="069de-131">`Size`.</span></span> <span data-ttu-id="069de-132">Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které systému uvolňování paměti počítá kořeny objektu.</span><span class="sxs-lookup"><span data-stu-id="069de-132">If the `type` is `CorGCREferenceType.CorHandleStrongSizedByref`, this field is the last size of the object tree for which the garbage collector calculated the object roots.</span></span> <span data-ttu-id="069de-133">Všimněte si, že tento výpočet není nutně aktuální.</span><span class="sxs-lookup"><span data-stu-id="069de-133">Note that this calculation is not necessarily up to date.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069de-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="069de-134">Requirements</span></span>  
 <span data-ttu-id="069de-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="069de-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="069de-136">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="069de-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="069de-137">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="069de-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="069de-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="069de-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069de-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="069de-139">See also</span></span>

- [<span data-ttu-id="069de-140">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="069de-140">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="069de-141">Ladění</span><span class="sxs-lookup"><span data-stu-id="069de-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
