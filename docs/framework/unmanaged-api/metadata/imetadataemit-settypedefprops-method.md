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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddb40c3265b3f42514d9dbd6f620a783089a4fad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481172"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="7e8f3-102">IMetaDataEmit::SetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7e8f3-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="7e8f3-103">Nastaví funkce typu definované v předchozím volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e8f3-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e8f3-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e8f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e8f3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7e8f3-106">[in] `mdTypeDef` Token získaný z volání původní [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e8f3-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="7e8f3-107">[in] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="7e8f3-108">To je bitová maska z `CorTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="7e8f3-109">[in] `mdToken` Základní třídy.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="7e8f3-110">Získané z předchozího volání [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="7e8f3-111">[in] Pole tokenů pro rozhraní, která tento typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="7e8f3-112">Tyto `mdTypeRef` tokeny jsou získány pomocí [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e8f3-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="7e8f3-113">Poslední prvek pole musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="7e8f3-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e8f3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e8f3-114">Requirements</span></span>  
 <span data-ttu-id="7e8f3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e8f3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e8f3-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e8f3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e8f3-117">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e8f3-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e8f3-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e8f3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8f3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e8f3-119">See also</span></span>
- [<span data-ttu-id="7e8f3-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e8f3-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7e8f3-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e8f3-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
