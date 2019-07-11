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
ms.openlocfilehash: a4185ec41fc9f7d1d919a79b57c02625210ad72a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777190"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="4d660-102">IMetaDataEmit2::DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="4d660-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="4d660-103">Vytvoří instanci obecné metody a získá token pro definici.</span><span class="sxs-lookup"><span data-stu-id="4d660-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d660-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d660-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d660-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="4d660-106">[in] Token pro metodu z nich pro vytvoření obecného instance.</span><span class="sxs-lookup"><span data-stu-id="4d660-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="4d660-107">Token musí být typu `mdMethodDef` nebo `mdMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="4d660-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4d660-108">[in] Ukazatel na binární modelu COM + podpis metody.</span><span class="sxs-lookup"><span data-stu-id="4d660-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="4d660-109">[in] Velikost v bajtech, z `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="4d660-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="4d660-110">[out] Token k definici metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="4d660-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d660-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d660-111">Requirements</span></span>  
 <span data-ttu-id="4d660-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d660-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d660-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d660-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d660-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d660-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d660-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d660-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d660-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d660-116">See also</span></span>

- [<span data-ttu-id="4d660-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d660-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4d660-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d660-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
