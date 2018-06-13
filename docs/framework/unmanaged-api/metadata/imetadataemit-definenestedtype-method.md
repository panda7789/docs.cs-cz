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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447000"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="483e7-102">IMetaDataEmit::DefineNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="483e7-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="483e7-103">Vytvoří metadata podpis definice typu, vrátí `mdTypeDef` token pro tento typ a určuje, že je definovaný typ člena typu odkazuje `tdEncloser` parametr.</span><span class="sxs-lookup"><span data-stu-id="483e7-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="483e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="483e7-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="483e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="483e7-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="483e7-106">[v] Název typu ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="483e7-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="483e7-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="483e7-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="483e7-108">Toto je bitová maska s `CorTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="483e7-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="483e7-109">[v] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="483e7-109">[in] The token of the base class.</span></span> <span data-ttu-id="483e7-110">To znamená buď `mdTypeDef` nebo `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="483e7-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="483e7-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="483e7-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="483e7-112">[v] Pole tokeny, které určují, rozhraní, která implementuje této třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="483e7-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="483e7-113">[v] Token nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="483e7-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="483e7-114">Musí být posledním prvkem pole `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="483e7-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="483e7-115">[out] `mdTypeDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="483e7-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="483e7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="483e7-116">Requirements</span></span>  
 <span data-ttu-id="483e7-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="483e7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="483e7-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="483e7-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="483e7-119">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="483e7-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="483e7-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="483e7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483e7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="483e7-121">See Also</span></span>  
 [<span data-ttu-id="483e7-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="483e7-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="483e7-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="483e7-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
