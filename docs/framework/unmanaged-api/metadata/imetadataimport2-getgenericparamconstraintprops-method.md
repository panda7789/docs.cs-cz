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
ms.openlocfilehash: c1d76dcd581b54d54d6b44505e09476993b2930c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446814"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="fbc9b-102">IMetaDataImport2::GetGenericParamConstraintProps – metoda</span><span class="sxs-lookup"><span data-stu-id="fbc9b-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="fbc9b-103">Získá metadata spojená s omezením obecný parametr reprezentována token zadané omezení.</span><span class="sxs-lookup"><span data-stu-id="fbc9b-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbc9b-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbc9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbc9b-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="fbc9b-106">[v] Token k omezení obecný parametr, pro které chcete vrátit metadata.</span><span class="sxs-lookup"><span data-stu-id="fbc9b-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="fbc9b-107">[out] Ukazatel na token, který reprezentuje obecný parametr, který je omezen.</span><span class="sxs-lookup"><span data-stu-id="fbc9b-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="fbc9b-108">[out] Ukazatel na TypeDef, Odkaz TypeRef nebo typ TypeSpec token, který představuje omezení na `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="fbc9b-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc9b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbc9b-109">Requirements</span></span>  
 <span data-ttu-id="fbc9b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc9b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc9b-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fbc9b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbc9b-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fbc9b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fbc9b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc9b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc9b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbc9b-114">See Also</span></span>  
 [<span data-ttu-id="fbc9b-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbc9b-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="fbc9b-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbc9b-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
