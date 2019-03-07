---
title: IMetaDataEmit::DefineImportMember – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ac44d29dd99e0205c515905f9846263033babf3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479295"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="44147-102">IMetaDataEmit::DefineImportMember – metoda</span><span class="sxs-lookup"><span data-stu-id="44147-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="44147-103">Vytvoří odkaz na zadaný člen typ nebo modul je definované mimo aktuální obor, který definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="44147-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44147-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44147-104">Syntax</span></span>  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44147-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44147-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="44147-106">[in] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ze kterého cílový člen importovány.</span><span class="sxs-lookup"><span data-stu-id="44147-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="44147-107">[in] Pole, která obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="44147-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="44147-108">[in] Počet bajtů `pbHashValue` pole.</span><span class="sxs-lookup"><span data-stu-id="44147-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="44147-109">[in] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje obor metadat, ze kterého cílový člen importovány.</span><span class="sxs-lookup"><span data-stu-id="44147-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="44147-110">[in] Token metadat, která určuje, že cílový člen.</span><span class="sxs-lookup"><span data-stu-id="44147-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="44147-111">Token, který může být `mdMethodDef` (pro metodu member), `mdProperty` (pro vlastnost člena), nebo `mdFieldDef` (pro člena pole) token.</span><span class="sxs-lookup"><span data-stu-id="44147-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="44147-112">[in] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého se importují cílový člen.</span><span class="sxs-lookup"><span data-stu-id="44147-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="44147-113">[in] `mdTypeRef` Nebo `mdModuleRef` token pro tento typ nebo modul, v uvedeném pořadí, které vlastní cílový člen.</span><span class="sxs-lookup"><span data-stu-id="44147-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="44147-114">[out] `mdMemberRef` Token, který je definován v oboru pro odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="44147-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44147-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44147-115">Remarks</span></span>  
 <span data-ttu-id="44147-116">`DefineImportMember` Metoda vyhledá člen určené `mbMember`, která je definována v jiném rozsahu určeném `pImport`a načte její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="44147-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="44147-117">Použije tyto informace k volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda v aktuálním rozsahu. Chcete-li vytvořit odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="44147-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="44147-118">Obecně platí, před použitím `DefineImportMember` metoda, je nutné vytvořit, v aktuálním oboru, odkaz na typ nebo odkaz na modul pro cílový člen nadřazené třídy, rozhraní nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="44147-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="44147-119">Token metadat pro tento odkaz je pak předán `tkParent` argument.</span><span class="sxs-lookup"><span data-stu-id="44147-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="44147-120">Není nutné vytvořit odkaz na nadřazený cílový člen, pokud se dá vyřešit později kompilátoru nebo linkeru.</span><span class="sxs-lookup"><span data-stu-id="44147-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="44147-121">Shrnutí:</span><span class="sxs-lookup"><span data-stu-id="44147-121">To summarize:</span></span>  
  
-   <span data-ttu-id="44147-122">Pokud cílový člen je pole nebo metoda, použijte buď [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodu pro vytvoření odkazu typu v aktuálním oboru pro nadřazené třídu nebo rozhraní nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="44147-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
-   <span data-ttu-id="44147-123">Pokud cílový člen je globální proměnnou nebo globální funkce (to znamená, není členem třídy nebo rozhraní), použijte [imetadataemit::definemoduleref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodu pro vytvoření odkazu na modul v aktuálním oboru pro nadřazeného člena modul.</span><span class="sxs-lookup"><span data-stu-id="44147-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
-   <span data-ttu-id="44147-124">Pokud cílový člen nadřazené vyřeší později kompilátoru nebo linkeru, pak předejte `mdTokenNil` v `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="44147-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="44147-125">To platí pouze scénář, je při globální funkce nebo globální proměnná je importována ze souboru .obj, který bude nakonec propojené s aktuální modul a sloučí metadata.</span><span class="sxs-lookup"><span data-stu-id="44147-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44147-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44147-126">Requirements</span></span>  
 <span data-ttu-id="44147-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44147-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44147-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44147-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44147-129">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44147-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44147-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44147-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44147-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44147-131">See also</span></span>
- [<span data-ttu-id="44147-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44147-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="44147-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44147-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
