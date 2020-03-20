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
ms.openlocfilehash: a7449ffc8a8ccf2db62ab3cff2f9cfaffd0c72a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175860"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="3f922-102">IMetaDataEmit::DefineImportMember – metoda</span><span class="sxs-lookup"><span data-stu-id="3f922-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="3f922-103">Vytvoří odkaz na zadaný člen typu nebo modulu, který je definován mimo aktuální obor a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="3f922-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f922-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f922-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="3f922-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f922-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="3f922-106">[v] Rozhraní [IMetaDataAssemblyImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) které představuje sestavení, ze kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="3f922-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3f922-107">[v] Pole, které obsahuje hash pro `pAssemImport`sestavení určené .</span><span class="sxs-lookup"><span data-stu-id="3f922-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3f922-108">[v] Počet bajtů v `pbHashValue` poli.</span><span class="sxs-lookup"><span data-stu-id="3f922-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="3f922-109">[v] Rozhraní [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) které představuje obor metadat, ze kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="3f922-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="3f922-110">[v] Token metadat, který určuje cílový člen.</span><span class="sxs-lookup"><span data-stu-id="3f922-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="3f922-111">Token může být `mdMethodDef` token (pro `mdProperty` metodu člena), (pro vlastnost člena) nebo `mdFieldDef` (pro členské pole) token.</span><span class="sxs-lookup"><span data-stu-id="3f922-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="3f922-112">[v] Rozhraní [IMetaDataAssemblyEmit,](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) které představuje sestavení, do kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="3f922-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="3f922-113">[v] `mdModuleRef` Nebo `mdTypeRef` token pro typ nebo modul, respektive, který vlastní cílový člen.</span><span class="sxs-lookup"><span data-stu-id="3f922-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="3f922-114">[out] Token, `mdMemberRef` který je definován v aktuálním oboru pro odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="3f922-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f922-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f922-115">Remarks</span></span>  
 <span data-ttu-id="3f922-116">Metoda `DefineImportMember` vyhledá člen, určený `mbMember`v , který je definován `pImport`v jiném oboru, určený v . a načte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3f922-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="3f922-117">Tyto informace používá k volání [metody IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) v aktuálním oboru k vytvoření odkazu na člena.</span><span class="sxs-lookup"><span data-stu-id="3f922-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="3f922-118">Obecně platí, že `DefineImportMember` před použitím metody je nutné vytvořit v aktuálním oboru odkaz na typ nebo odkaz na modul pro nadřazenou třídu, rozhraní nebo modul cílového člena.</span><span class="sxs-lookup"><span data-stu-id="3f922-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="3f922-119">Token metadat pro tento odkaz je `tkParent` pak předán v argumentu.</span><span class="sxs-lookup"><span data-stu-id="3f922-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="3f922-120">Není nutné vytvořit odkaz na nadřazený cílový člen, pokud bude vyřešen později kompilátorem nebo propojovacím sítí.</span><span class="sxs-lookup"><span data-stu-id="3f922-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="3f922-121">Shrnutí:</span><span class="sxs-lookup"><span data-stu-id="3f922-121">To summarize:</span></span>  
  
- <span data-ttu-id="3f922-122">Pokud je cílovým členem pole nebo metoda, použijte buď [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [Metodu IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) k vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3f922-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="3f922-123">Pokud cílový člen je globální proměnná nebo globální funkce (to znamená, že není členem třídy nebo rozhraní), použijte [metodu IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) k vytvoření odkazu na modul v aktuálním oboru pro nadřazený modul člena.</span><span class="sxs-lookup"><span data-stu-id="3f922-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="3f922-124">Pokud nadřazený cílový člen bude vyřešen později kompilátorem nebo propojovacím sítí, pak předajte `mdTokenNil` `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="3f922-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="3f922-125">Jediný scénář, ve kterém to platí je, když globální funkce nebo globální proměnná je importován ze souboru OBJ, který bude nakonec propojeny do aktuálního modulu a metadata sloučena.</span><span class="sxs-lookup"><span data-stu-id="3f922-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f922-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f922-126">Requirements</span></span>  
 <span data-ttu-id="3f922-127">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f922-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f922-128">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3f922-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f922-129">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f922-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f922-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f922-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f922-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f922-131">See also</span></span>

- [<span data-ttu-id="3f922-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f922-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f922-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f922-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
