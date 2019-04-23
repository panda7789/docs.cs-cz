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
ms.openlocfilehash: ce6df232f3793b8b61d9fa7c18c9c90ca9fa3900
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184714"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="dd31b-102">IMetaDataEmit2::DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="dd31b-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="dd31b-103">Vytvoří instanci obecné metody a získá token pro definici.</span><span class="sxs-lookup"><span data-stu-id="dd31b-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd31b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd31b-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd31b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd31b-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="dd31b-106">[in] Token pro metodu z nich pro vytvoření obecného instance.</span><span class="sxs-lookup"><span data-stu-id="dd31b-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="dd31b-107">Token musí být typu `mdMethodDef` nebo `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="dd31b-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="dd31b-108">[in] Ukazatel na binární modelu COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="dd31b-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="dd31b-109">[in] Velikost v bajtech, z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="dd31b-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="dd31b-110">[out] Token k definici metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="dd31b-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd31b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd31b-111">Requirements</span></span>  
 <span data-ttu-id="dd31b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd31b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd31b-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd31b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd31b-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd31b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd31b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd31b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd31b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd31b-116">See also</span></span>

- [<span data-ttu-id="dd31b-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd31b-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="dd31b-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd31b-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
