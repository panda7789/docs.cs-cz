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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004351"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="bf77a-102">IMetaDataEmit::DefineNestedType – metoda</span><span class="sxs-lookup"><span data-stu-id="bf77a-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="bf77a-103">Vytvoří podpis metadat definice typu, vrátí `mdTypeDef` token pro daný typ a určí, že definovaný typ je členem typu, na který odkazuje `tdEncloser` parametr.</span><span class="sxs-lookup"><span data-stu-id="bf77a-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf77a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf77a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bf77a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf77a-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="bf77a-106">pro Název typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bf77a-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="bf77a-107">[in] `TypeDef` atribut.</span><span class="sxs-lookup"><span data-stu-id="bf77a-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="bf77a-108">Toto je Bitová maska `CorTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="bf77a-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="bf77a-109">pro Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bf77a-109">[in] The token of the base class.</span></span> <span data-ttu-id="bf77a-110">Toto je buď `mdTypeDef` token, nebo `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="bf77a-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="bf77a-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="bf77a-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="bf77a-112">pro Pole tokenů, které určují rozhraní, které tato třída nebo rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="bf77a-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="bf77a-113">pro Token ohraničujícího typu</span><span class="sxs-lookup"><span data-stu-id="bf77a-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="bf77a-114">Poslední prvek pole musí být `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="bf77a-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="bf77a-115">mimo `mdTypeDef`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="bf77a-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf77a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf77a-116">Requirements</span></span>  
 <span data-ttu-id="bf77a-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf77a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf77a-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bf77a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf77a-119">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bf77a-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf77a-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf77a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf77a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf77a-121">See also</span></span>

- [<span data-ttu-id="bf77a-122">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf77a-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bf77a-123">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf77a-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
