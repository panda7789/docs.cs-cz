---
title: IMetaDataEmit::SetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177467"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="68610-102">IMetaDataEmit::SetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="68610-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="68610-103">Nastaví funkce typu definovaného předchozím voláním [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="68610-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68610-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68610-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68610-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68610-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="68610-106">[v] Token `mdTypeDef` získaný z původního volání [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="68610-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="68610-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="68610-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="68610-108">Toto je bitová maska `CorTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="68610-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="68610-109">[v] Základní `mdToken` třídy.</span><span class="sxs-lookup"><span data-stu-id="68610-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="68610-110">Získané z předchozího volání [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="68610-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="68610-111">[v] Pole tokenů pro rozhraní, které tento typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="68610-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="68610-112">Tyto `mdTypeRef` tokeny jsou získány pomocí [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="68610-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="68610-113">Poslední prvek pole musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="68610-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68610-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68610-114">Requirements</span></span>  
 <span data-ttu-id="68610-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68610-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68610-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="68610-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68610-117">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68610-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68610-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68610-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68610-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="68610-119">See also</span></span>

- [<span data-ttu-id="68610-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68610-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="68610-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68610-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
