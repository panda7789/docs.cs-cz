---
title: "IMetaDataEmit::MergeEnd – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 57fbecd05f0eaee48e9dc8a599e3174ac97033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="4a171-102">IMetaDataEmit::MergeEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="4a171-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="4a171-103">Sloučení do aktuální obor všechny obory metadata určeného jeden nebo více předchozích volání [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="4a171-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a171-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a171-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a171-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a171-105">Parameters</span></span>  
 <span data-ttu-id="4a171-106">Tato metoda nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="4a171-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a171-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a171-107">Remarks</span></span>  
 <span data-ttu-id="4a171-108">Tato rutina aktivuje skutečné sloučení metadat, všechny importovat rozsahy určené tak, že před volání `IMetaDataEmit::Merge`, do aktuálního oboru výstup.</span><span class="sxs-lookup"><span data-stu-id="4a171-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="4a171-109">Následující zvláštní podmínky platí pro sloučení:</span><span class="sxs-lookup"><span data-stu-id="4a171-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="4a171-110">Identifikátor verze modulu (identifikátoru MVID) je nikdy importován, protože je jedinečné pro metadata v oboru importu.</span><span class="sxs-lookup"><span data-stu-id="4a171-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="4a171-111">Žádné existující vlastnosti modulu celou se přepíší.</span><span class="sxs-lookup"><span data-stu-id="4a171-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="4a171-112">Pokud modul vlastnosti byly nastaveny pro aktuální obor, žádné vlastnosti modulu importují.</span><span class="sxs-lookup"><span data-stu-id="4a171-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="4a171-113">Nicméně pokud nebyly nastaveny vlastnosti modulu v aktuálním oboru, jsou importované jen jednou, pokud se při prvním výskytu.</span><span class="sxs-lookup"><span data-stu-id="4a171-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="4a171-114">Pokud tyto vlastnosti modulu nedojde k znovu, jsou duplicitní.</span><span class="sxs-lookup"><span data-stu-id="4a171-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="4a171-115">Pokud porovnání hodnot všech vlastností modulu (s výjimkou identifikátoru MVID) a jsou nalezeny žádné duplicitní hodnoty, je vyvolána k chybě.</span><span class="sxs-lookup"><span data-stu-id="4a171-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="4a171-116">Pro definice typů (`TypeDef`), neobsahuje žádné duplikáty jsou sloučeny do aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="4a171-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="4a171-117">`TypeDef`objekty jsou kontrolovány duplikátů proti jednotlivým *objekt plně kvalifikovaný název* + *GUID* + *číslo verze*.</span><span class="sxs-lookup"><span data-stu-id="4a171-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="4a171-118">Pokud není nalezena shoda na název nebo identifikátor GUID, a všechny další dva elementy se liší, je vyvolána k chybě.</span><span class="sxs-lookup"><span data-stu-id="4a171-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="4a171-119">Jinak, pokud se všechny tři položky shodují, `MergeEnd` provede zběžnou kontrolu, ujistěte se, pak jsou skutečně duplikáty; v opačném případě se vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="4a171-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="4a171-120">Kontrola zběžnou vyhledá:</span><span class="sxs-lookup"><span data-stu-id="4a171-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="4a171-121">Stejném deklarace členů, ke kterým dochází ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4a171-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="4a171-122">Členové, které jsou označeny jako `mdPrivateScope` (najdete v článku [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) – výčet) nejsou součástí této kontroly; se speciálně sloučí.</span><span class="sxs-lookup"><span data-stu-id="4a171-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="4a171-123">Se stejné rozvržení třídy.</span><span class="sxs-lookup"><span data-stu-id="4a171-123">The same class layout.</span></span>  
  
     <span data-ttu-id="4a171-124">To znamená, že `TypeDef` objekt musí vždy být plně a konzistentně definován v oboru každých metadata ve kterém je deklarovaná; pokud jeho implementace člen (pro třídu) jsou rozloženy několika kompilačních jednotek, se považuje za úplné definice v každé oboru a ne přírůstkové do každého oboru.</span><span class="sxs-lookup"><span data-stu-id="4a171-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="4a171-125">Například pokud názvy parametrů jsou relevantní pro kontrakt, se musí být vygenerované stejným způsobem jako do každé oboru; Pokud nejsou relevantní, by neměl být vložen do metadat.</span><span class="sxs-lookup"><span data-stu-id="4a171-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="4a171-126">Výjimkou je, že `TypeDef` objekt může mít přírůstkové členy označení `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="4a171-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="4a171-127">Na tyto zjištění `MergeEnd` přírůstkově se přidají do aktuálního oboru bez ohledu na duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="4a171-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="4a171-128">Protože kompilátor rozumí oboru privátní, musí být kompilátor zodpovědný za vynucení pravidel.</span><span class="sxs-lookup"><span data-stu-id="4a171-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="4a171-129">Relativní virtuální adresy (RVAs) nejsou importovány nebo sloučit; Kompilátor očekává se znovu generuje tato informace.</span><span class="sxs-lookup"><span data-stu-id="4a171-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="4a171-130">Vlastní atributy jsou sloučeny jenom v případě, že je sloučen položku, ke kterému jsou připojené.</span><span class="sxs-lookup"><span data-stu-id="4a171-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="4a171-131">Například vlastní atributy přidružené třídy jsou sloučeny, pokud je třída při prvním výskytu.</span><span class="sxs-lookup"><span data-stu-id="4a171-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="4a171-132">Pokud jsou vlastní atributy přidružené `TypeDef` nebo `MemberDef` týkající se jednotka kompilace (například časové razítko kompilace člen), není sloučeno a je maximálně kompilátoru odebrat nebo aktualizovat takové metadat.</span><span class="sxs-lookup"><span data-stu-id="4a171-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a171-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a171-133">Requirements</span></span>  
 <span data-ttu-id="4a171-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a171-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a171-135">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a171-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a171-136">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a171-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a171-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a171-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a171-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a171-138">See Also</span></span>  
 [<span data-ttu-id="4a171-139">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a171-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4a171-140">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a171-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
