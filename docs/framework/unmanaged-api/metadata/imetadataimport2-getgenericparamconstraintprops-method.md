---
title: IMetaDataImport2::GetGenericParamConstraintProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0503c5bd924793df8143c89e358618fb8844c6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215115"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="c446f-102">IMetaDataImport2::GetGenericParamConstraintProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c446f-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="c446f-103">Získá metadata přidružená k omezení obecného parametru reprezentována token zadané omezení.</span><span class="sxs-lookup"><span data-stu-id="c446f-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c446f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c446f-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c446f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c446f-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="c446f-106">[in] Token, který má omezení obecný parametr, pro které chcete vrátit metadata.</span><span class="sxs-lookup"><span data-stu-id="c446f-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="c446f-107">[out] Ukazatel na token, který představuje obecný parametr, který je omezen.</span><span class="sxs-lookup"><span data-stu-id="c446f-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="c446f-108">[out] Ukazatel na typ TypeSpec, – TypeDef nebo TypeRef token, který představuje omezení na `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="c446f-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c446f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c446f-109">Requirements</span></span>  
 <span data-ttu-id="c446f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c446f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c446f-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c446f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c446f-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c446f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c446f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c446f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c446f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c446f-114">See also</span></span>

- [<span data-ttu-id="c446f-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c446f-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="c446f-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c446f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
