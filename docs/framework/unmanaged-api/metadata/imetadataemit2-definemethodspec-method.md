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
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175535"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="1ebea-102">IMetaDataEmit2::DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="1ebea-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="1ebea-103">Vytvoří obecnou instanci metody a získá token k definici.</span><span class="sxs-lookup"><span data-stu-id="1ebea-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ebea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ebea-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ebea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ebea-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="1ebea-106">[v] Token pro metodu, která chcete vytvořit obecnou instanci.</span><span class="sxs-lookup"><span data-stu-id="1ebea-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="1ebea-107">Token musí být `mdMethodDef` typu `mdMemberRef`nebo .</span><span class="sxs-lookup"><span data-stu-id="1ebea-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1ebea-108">[v] Ukazatel na binární podpis metody modelu COM+.</span><span class="sxs-lookup"><span data-stu-id="1ebea-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="1ebea-109">[v] Velikost v bajtů `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1ebea-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="1ebea-110">[out] Token definice podpisu metadat metody.</span><span class="sxs-lookup"><span data-stu-id="1ebea-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ebea-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1ebea-111">Requirements</span></span>  
 <span data-ttu-id="1ebea-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ebea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ebea-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1ebea-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ebea-114">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ebea-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ebea-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ebea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebea-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ebea-116">See also</span></span>

- [<span data-ttu-id="1ebea-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ebea-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="1ebea-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1ebea-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
