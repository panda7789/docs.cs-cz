---
title: IMetaDataEmit2::DefineMethodSpec – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85b17199ad40d8b3fbf4e1a0271828e5a5ac7991
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445257"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="0415d-102">IMetaDataEmit2::DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="0415d-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="0415d-103">Vytvoří instanci obecné metody a získá token k definici.</span><span class="sxs-lookup"><span data-stu-id="0415d-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0415d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0415d-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0415d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0415d-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="0415d-106">[v] Token pro metodu pro vytvoření obecné instance.</span><span class="sxs-lookup"><span data-stu-id="0415d-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="0415d-107">Token musí být typu `mdMethodDef` nebo `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="0415d-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0415d-108">[v] Ukazatel na binární modelu COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="0415d-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="0415d-109">[v] Velikost v bajtech z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0415d-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="0415d-110">[out] Token pro definici metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="0415d-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0415d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0415d-111">Requirements</span></span>  
 <span data-ttu-id="0415d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0415d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0415d-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0415d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0415d-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0415d-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0415d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0415d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0415d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0415d-116">See Also</span></span>  
 [<span data-ttu-id="0415d-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0415d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="0415d-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0415d-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
