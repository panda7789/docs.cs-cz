---
title: "IMetaDataEmit::DefineImportMember – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d06bf7649f09b2111bf9a6840968743ad77bdca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="bfa69-102">IMetaDataEmit::DefineImportMember – metoda</span><span class="sxs-lookup"><span data-stu-id="bfa69-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="bfa69-103">Vytvoří odkaz na zadaný člen typu nebo modul, který je definován v aktuálním oboru a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="bfa69-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfa69-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="bfa69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfa69-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="bfa69-106">[v] [Imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní, které představuje sestavení, ze kterého je naimportované cílového člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="bfa69-107">[v] Pole, které obsahuje hodnotu hash pro sestavení určeného `pAssemImport`.</span><span class="sxs-lookup"><span data-stu-id="bfa69-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="bfa69-108">[v] Počet bajtů `pbHashValue` pole.</span><span class="sxs-lookup"><span data-stu-id="bfa69-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="bfa69-109">[v] [Imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní, které představuje metadata oboru, ze kterého je naimportována cílového člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="bfa69-110">[v] Metadata token, který určuje cíl člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="bfa69-111">Může být token `mdMethodDef` (pro metodu člen), `mdProperty` (pro vlastnost člena), nebo `mdFieldDef` (pro pole člen) tokenu.</span><span class="sxs-lookup"><span data-stu-id="bfa69-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="bfa69-112">[v] [Imetadataassemblyemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) rozhraní, které představuje sestavení, do kterého je naimportované cílového člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="bfa69-113">[v] `mdTypeRef` Nebo `mdModuleRef` tokenu pro modul nebo typ, v uvedeném pořadí, který je vlastníkem člen cíl.</span><span class="sxs-lookup"><span data-stu-id="bfa69-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="bfa69-114">[out] `mdMemberRef` Token, který je definován v aktuálním oboru pro odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfa69-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfa69-115">Remarks</span></span>  
 <span data-ttu-id="bfa69-116">`DefineImportMember` Metoda vyhledá člena, zadán `mbMember`, která je definována v jiném oboru určeného `pImport`a načte její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bfa69-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="bfa69-117">Tyto informace se použijí k volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda v aktuálním oboru vytvořit odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="bfa69-118">Obecně platí, před použitím `DefineImportMember` metoda, je nutné vytvořit, v aktuálním oboru, odkaz na typ nebo odkaz na modul pro nadřazené třídy, rozhraní nebo modul člen cíl.</span><span class="sxs-lookup"><span data-stu-id="bfa69-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="bfa69-119">Metadata token u tohoto odkazu je pak předaná `tkParent` argument.</span><span class="sxs-lookup"><span data-stu-id="bfa69-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="bfa69-120">Není nutné vytvořit odkaz na nadřazený člen cíl, pokud bude vyřešen později kompilátoru nebo linkeru.</span><span class="sxs-lookup"><span data-stu-id="bfa69-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="bfa69-121">Shrnutí:</span><span class="sxs-lookup"><span data-stu-id="bfa69-121">To summarize:</span></span>  
  
-   <span data-ttu-id="bfa69-122">Pokud je člen cílového pole nebo metoda, použijte buď [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) nebo [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) metodu pro vytvoření odkaz na typ, v aktuálním oboru pro nadřazené třídy nebo rozhraní nadřazeného člena.</span><span class="sxs-lookup"><span data-stu-id="bfa69-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
-   <span data-ttu-id="bfa69-123">Pokud je cílový člen globální proměnné nebo globální funkce (to znamená, nikoli pro člena třídy nebo rozhraní), použijte [imetadataemit::definemoduleref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) metodu pro vytvoření odkazu na modul v aktuálním oboru pro nadřazeného člena modul.</span><span class="sxs-lookup"><span data-stu-id="bfa69-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
-   <span data-ttu-id="bfa69-124">Pokud cílový člen nadřazené vyřeší později kompilátoru nebo linkeru, pak předejte `mdTokenNil` v `tkParent`.</span><span class="sxs-lookup"><span data-stu-id="bfa69-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="bfa69-125">Jediný scénář, ve kterém platí je při globální funkce nebo – globální proměnná importována ze souboru .obj, který se nakonec propojené do aktuální modul a metadata sloučit.</span><span class="sxs-lookup"><span data-stu-id="bfa69-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa69-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bfa69-126">Requirements</span></span>  
 <span data-ttu-id="bfa69-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa69-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa69-128">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bfa69-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bfa69-129">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bfa69-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfa69-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa69-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa69-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfa69-131">See Also</span></span>  
 [<span data-ttu-id="bfa69-132">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfa69-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="bfa69-133">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bfa69-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
