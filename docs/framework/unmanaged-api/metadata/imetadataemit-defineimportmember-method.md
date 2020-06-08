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
ms.openlocfilehash: 2facc63023a20dd6aaac64d7d036324c31658bc8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501310"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="34fd8-102">IMetaDataEmit::DefineImportMember – metoda</span><span class="sxs-lookup"><span data-stu-id="34fd8-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="34fd8-103">Vytvoří odkaz na zadaného člena typu nebo modulu, který je definován mimo aktuální obor, a definuje token pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="34fd8-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34fd8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="34fd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34fd8-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="34fd8-106">pro Rozhraní [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , které představuje sestavení, ze kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="34fd8-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="34fd8-107">pro Pole, které obsahuje hodnotu hash pro sestavení určené parametrem `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="34fd8-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="34fd8-108">pro Počet bajtů v `pbHashValue` poli.</span><span class="sxs-lookup"><span data-stu-id="34fd8-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="34fd8-109">pro Rozhraní [IMetaDataImport](imetadataimport-interface.md) , které představuje obor metadat, ze kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="34fd8-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="34fd8-110">pro Token metadat, který určuje cílového člena.</span><span class="sxs-lookup"><span data-stu-id="34fd8-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="34fd8-111">Token může být `mdMethodDef` (pro metodu člena), `mdProperty` (pro vlastnost člena) nebo `mdFieldDef` (pro pole člena).</span><span class="sxs-lookup"><span data-stu-id="34fd8-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="34fd8-112">pro Rozhraní [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) , které představuje sestavení, do kterého je importován cílový člen.</span><span class="sxs-lookup"><span data-stu-id="34fd8-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="34fd8-113">pro `mdTypeRef`Token nebo `mdModuleRef` pro typ nebo modul, v uvedeném pořadí, který vlastní cílového člena.</span><span class="sxs-lookup"><span data-stu-id="34fd8-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="34fd8-114">mimo `mdMemberRef`Token, který je definován v aktuálním oboru pro odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="34fd8-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34fd8-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34fd8-115">Remarks</span></span>  
 <span data-ttu-id="34fd8-116">`DefineImportMember`Metoda vyhledá člena, určeného parametrem `mbMember` , který je definován v jiném oboru, určeného parametrem `pImport` a načte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="34fd8-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="34fd8-117">Tato informace používá k volání metody [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md) v aktuálním oboru pro vytvoření odkazu na člena.</span><span class="sxs-lookup"><span data-stu-id="34fd8-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="34fd8-118">Obecně platí, že před použitím `DefineImportMember` metody musíte vytvořit v aktuálním oboru odkaz na typ nebo odkaz na modul pro nadřazenou třídu cílového člena, rozhraní nebo modul.</span><span class="sxs-lookup"><span data-stu-id="34fd8-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="34fd8-119">Token metadat pro tento odkaz je pak předán v `tkParent` argumentu.</span><span class="sxs-lookup"><span data-stu-id="34fd8-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="34fd8-120">Není nutné vytvářet odkaz na nadřazený člen cílového člena, pokud bude vyřešen později kompilátorem nebo linkerem.</span><span class="sxs-lookup"><span data-stu-id="34fd8-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="34fd8-121">Shrnutí:</span><span class="sxs-lookup"><span data-stu-id="34fd8-121">To summarize:</span></span>  
  
- <span data-ttu-id="34fd8-122">Pokud je cílový člen pole nebo metoda, použijte buď metodu [IMetaDataEmit::D efinetyperefbyname](imetadataemit-definetyperefbyname-method.md) , nebo [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md) pro vytvoření odkazu na typ v aktuálním oboru pro nadřazenou třídu člena nebo nadřazené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="34fd8-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
- <span data-ttu-id="34fd8-123">Pokud je cílový člen globální proměnnou nebo globální funkcí (tj. není členem třídy nebo rozhraní), použijte metodu [IMetaDataEmit::D efinemoduleref](imetadataemit-definemoduleref-method.md) pro vytvoření odkazu na modul v aktuálním oboru pro nadřazený modul člena.</span><span class="sxs-lookup"><span data-stu-id="34fd8-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
- <span data-ttu-id="34fd8-124">Pokud cíl cílového člena bude vyřešen později kompilátorem nebo linkerem, pak předejte `mdTokenNil` `tkParent` .</span><span class="sxs-lookup"><span data-stu-id="34fd8-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="34fd8-125">Jediným scénářem, ve kterém se to týká, je, že globální funkce nebo globální proměnná se importují ze souboru. obj, který bude nakonec propojený s aktuálním modulem a Sloučená metadata.</span><span class="sxs-lookup"><span data-stu-id="34fd8-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34fd8-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34fd8-126">Requirements</span></span>  
 <span data-ttu-id="34fd8-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34fd8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34fd8-128">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="34fd8-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34fd8-129">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="34fd8-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34fd8-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34fd8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fd8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34fd8-131">See also</span></span>

- [<span data-ttu-id="34fd8-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34fd8-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="34fd8-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34fd8-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
