---
title: "IMetaDataEmit::SetTypeDefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50f92d0ff307621695887ee7a0af2d4d19985f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="8ef40-102">IMetaDataEmit::SetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8ef40-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="8ef40-103">Nastaví funkce typu definované předchozí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ef40-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ef40-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ef40-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8ef40-106">[v] `mdTypeDef` Token získaný původní volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ef40-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="8ef40-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="8ef40-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="8ef40-108">Toto je bitová maska s `CorTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8ef40-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="8ef40-109">[v] `mdToken` Základní třídy.</span><span class="sxs-lookup"><span data-stu-id="8ef40-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="8ef40-110">Získané z předchozího volání [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), nebo `null`.</span><span class="sxs-lookup"><span data-stu-id="8ef40-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="8ef40-111">[v] Pole tokeny pro rozhraní, která implementuje tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8ef40-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="8ef40-112">Tyto `mdTypeRef` tokeny jsou získány pomocí [imetadataemit::defineimporttype –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="8ef40-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="8ef40-113">Je posledním elementem pole musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="8ef40-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef40-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ef40-114">Requirements</span></span>  
 <span data-ttu-id="8ef40-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ef40-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef40-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ef40-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ef40-117">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ef40-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ef40-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef40-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef40-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ef40-119">See Also</span></span>  
 [<span data-ttu-id="8ef40-120">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef40-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8ef40-121">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ef40-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
