---
title: IMetaDataEmit::MergeEnd – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45d85be4e4987e5a5234ca2d57c85a56f9f544bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657022"
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="c38b1-102">IMetaDataEmit::MergeEnd – metoda</span><span class="sxs-lookup"><span data-stu-id="c38b1-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="c38b1-103">Sloučení do aktuální obor oborů metadat zadán jeden nebo více předchozích volání [imetadataemit::merge –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span><span class="sxs-lookup"><span data-stu-id="c38b1-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c38b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c38b1-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c38b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c38b1-105">Parameters</span></span>  
 <span data-ttu-id="c38b1-106">Tato metoda nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="c38b1-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c38b1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c38b1-107">Remarks</span></span>  
 <span data-ttu-id="c38b1-108">Tato rutina spustí skutečné sloučení metadat, všech importovat obory zadané před volání `IMetaDataEmit::Merge`, do aktuálního oboru výstup.</span><span class="sxs-lookup"><span data-stu-id="c38b1-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="c38b1-109">Sloučení platí následující zvláštní podmínky:</span><span class="sxs-lookup"><span data-stu-id="c38b1-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="c38b1-110">Identifikátor verze modulu (identifikátor MVID) je nikdy importován, protože je jedinečný v oboru importu metadat.</span><span class="sxs-lookup"><span data-stu-id="c38b1-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="c38b1-111">Žádné existující vlastnosti celý modul přepsány.</span><span class="sxs-lookup"><span data-stu-id="c38b1-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="c38b1-112">Pokud již nebyly nastaveny vlastnosti modulu pro aktuální obor, žádné vlastnosti modulu importují.</span><span class="sxs-lookup"><span data-stu-id="c38b1-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="c38b1-113">Nicméně pokud nebyly nastaveny vlastnosti modulu v aktuálním oboru, jejich importování pouze jednou, při jejich prvním výskytu.</span><span class="sxs-lookup"><span data-stu-id="c38b1-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="c38b1-114">Pokud tyto vlastnosti modulu nedojde k znovu, jsou duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="c38b1-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="c38b1-115">Pokud jsou porovnány hodnoty všech vlastností modulu (s výjimkou identifikátor MVID) a nenajdou žádné duplicity, je vyvolána k chybě.</span><span class="sxs-lookup"><span data-stu-id="c38b1-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="c38b1-116">Typ definice (`TypeDef`), žádné duplicitní hodnoty jsou sloučeny do aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="c38b1-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="c38b1-117">`TypeDef` objekty jsou zkontrolovat duplicitu jednotlivá *objekt plně kvalifikovaný název* + *GUID* + *číslo verze*.</span><span class="sxs-lookup"><span data-stu-id="c38b1-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="c38b1-118">Pokud není nalezena shoda pro název nebo identifikátor GUID a některý další dva elementy se liší, je vyvolána k chybě.</span><span class="sxs-lookup"><span data-stu-id="c38b1-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="c38b1-119">Jinak, pokud se shodují všechny tři položky `MergeEnd` provede zběžné kontrolu, aby položky jsou ve skutečnosti duplicitní; v opačném případě dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="c38b1-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="c38b1-120">Zběžné Kontrola vyhledá:</span><span class="sxs-lookup"><span data-stu-id="c38b1-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="c38b1-121">Stejný člen prohlášení, ke kterým dochází ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c38b1-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="c38b1-122">Členy, které jsou označeny jako `mdPrivateScope` (najdete v článku [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet) nejsou součástí této kontroly; jsou speciálně sloučeny.</span><span class="sxs-lookup"><span data-stu-id="c38b1-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="c38b1-123">Stejné rozložení třídy.</span><span class="sxs-lookup"><span data-stu-id="c38b1-123">The same class layout.</span></span>  
  
     <span data-ttu-id="c38b1-124">To znamená, že `TypeDef` objektu musí vždy plně a konzistentně definovat v každé metadata rozsahu ve kterém je deklarována, pokud jeho implementace členů (pro třídu) jsou rozděleny mezi několika kompilačních jednotek, úplná definice se předpokládá se, že k dispozici v každé oboru, ne přírůstková k jednotlivým oborům.</span><span class="sxs-lookup"><span data-stu-id="c38b1-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="c38b1-125">Například pokud názvy parametrů jsou relevantní pro kontrakt, se musí emitovat stejným způsobem jako do každé obor; Pokud nejsou relevantní, by neměly být vložen do metadat.</span><span class="sxs-lookup"><span data-stu-id="c38b1-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="c38b1-126">Výjimkou je, že `TypeDef` , může být označený jako přírůstkové členy `mdPrivateScope`.</span><span class="sxs-lookup"><span data-stu-id="c38b1-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="c38b1-127">Na tyto, zjištění `MergeEnd` postupně se přidají do aktuálního oboru bez ohledu na duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="c38b1-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="c38b1-128">Protože kompilátor rozpozná oboru privátní, kompilátor musí být za vynucování pravidel.</span><span class="sxs-lookup"><span data-stu-id="c38b1-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="c38b1-129">Relativních virtuálních adres (RVA) nejsou importovány nebo sloučit; Kompilátor by měl znovu vygenerovat tyto informace.</span><span class="sxs-lookup"><span data-stu-id="c38b1-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="c38b1-130">Vlastní atributy jsou sloučeny pouze v případě, že se sloučí položku, ke kterému jsou připojené.</span><span class="sxs-lookup"><span data-stu-id="c38b1-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="c38b1-131">Například vlastní atributy přidružené třídy jsou sloučeny při prvním výskytu třídy se.</span><span class="sxs-lookup"><span data-stu-id="c38b1-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="c38b1-132">Pokud uživatelských atributů, které jsou přidruženy `TypeDef` nebo `MemberDef` , která je specifická pro kompilační jednotky (například časové razítko člen kompilace), nejsou sloučené a je kompilátor odebrat nebo aktualizovat tato metadata.</span><span class="sxs-lookup"><span data-stu-id="c38b1-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c38b1-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c38b1-133">Requirements</span></span>  
 <span data-ttu-id="c38b1-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c38b1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c38b1-135">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c38b1-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c38b1-136">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c38b1-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c38b1-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c38b1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c38b1-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c38b1-138">See also</span></span>
- [<span data-ttu-id="c38b1-139">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c38b1-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c38b1-140">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c38b1-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
