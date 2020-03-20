---
title: IMetaDataEmit::DefineNestedType – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175808"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="04c18-102">IMetaDataEmit::DefineNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="04c18-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="04c18-103">Vytvoří podpis metadat definice typu, vrátí `mdTypeDef` token pro tento typ a určuje, že definovaný typ je `tdEncloser` členem typu, na který parametr odkazuje.</span><span class="sxs-lookup"><span data-stu-id="04c18-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04c18-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04c18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04c18-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="04c18-106">[v] Název typu v Unicode.</span><span class="sxs-lookup"><span data-stu-id="04c18-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="04c18-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="04c18-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="04c18-108">Toto je bitová maska `CorTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="04c18-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="04c18-109">[v] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="04c18-109">[in] The token of the base class.</span></span> <span data-ttu-id="04c18-110">Toto je `mdTypeDef` buď `mdTypeRef` token nebo.</span><span class="sxs-lookup"><span data-stu-id="04c18-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="04c18-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="04c18-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="04c18-112">[v] Pole tokenů, které určují rozhraní, které tato třída nebo rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="04c18-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="04c18-113">[v] Token ohraničujícího typu.</span><span class="sxs-lookup"><span data-stu-id="04c18-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="04c18-114">Poslední prvek pole musí `mdTokenNil`být .</span><span class="sxs-lookup"><span data-stu-id="04c18-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="04c18-115">[out] Přiřazen `mdTypeDef` token.</span><span class="sxs-lookup"><span data-stu-id="04c18-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04c18-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04c18-116">Requirements</span></span>  
 <span data-ttu-id="04c18-117">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04c18-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04c18-118">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="04c18-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04c18-119">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04c18-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04c18-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04c18-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c18-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="04c18-121">See also</span></span>

- [<span data-ttu-id="04c18-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04c18-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="04c18-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04c18-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
