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
ms.openlocfilehash: da52d540266e2c5f9bfc7f1a83d2683fa765914b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478745"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="da43a-102">IMetaDataEmit::DefineNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="da43a-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="da43a-103">Vytvoří metadata podpis definici typu, vrátí `mdTypeDef` token pro daný typ a určí, že definovaný typ je členem typu odkazuje `tdEncloser` parametru.</span><span class="sxs-lookup"><span data-stu-id="da43a-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da43a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da43a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="da43a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da43a-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="da43a-106">[in] Název typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="da43a-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="da43a-107">[in] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="da43a-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="da43a-108">To je bitová maska z `CorTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="da43a-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="da43a-109">[in] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="da43a-109">[in] The token of the base class.</span></span> <span data-ttu-id="da43a-110">Je to `mdTypeDef` nebo `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="da43a-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="da43a-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="da43a-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="da43a-112">[in] Pole tokeny, které určují, které tuto třídu nebo rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="da43a-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="da43a-113">[in] Token nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="da43a-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="da43a-114">Poslední element pole musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="da43a-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="da43a-115">[out] `mdTypeDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="da43a-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da43a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da43a-116">Requirements</span></span>  
 <span data-ttu-id="da43a-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da43a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da43a-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da43a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da43a-119">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da43a-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da43a-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da43a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da43a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da43a-121">See also</span></span>
- [<span data-ttu-id="da43a-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da43a-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="da43a-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da43a-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
