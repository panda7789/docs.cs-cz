---
title: IMetaDataEmit::DefineCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175886"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="c5901-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="c5901-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="c5901-103">Vytvoří definici vlastního atributu se zadaným podpisem metadat, který má být připojen k zadanému objektu, a získá token k této vlastní definici atributu.</span><span class="sxs-lookup"><span data-stu-id="c5901-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5901-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5901-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5901-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5901-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="c5901-106">[v] Token pro položku vlastníka.</span><span class="sxs-lookup"><span data-stu-id="c5901-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c5901-107">[v] Token, který identifikuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="c5901-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="c5901-108">[v] Ukazatel na vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="c5901-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="c5901-109">[v] Počet bajtů v `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="c5901-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="c5901-110">[out] Přiřazen `mdCustomAttribute` token.</span><span class="sxs-lookup"><span data-stu-id="c5901-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5901-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5901-111">Requirements</span></span>  
 <span data-ttu-id="c5901-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5901-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5901-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c5901-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5901-114">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5901-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5901-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5901-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5901-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5901-116">See also</span></span>

- [<span data-ttu-id="c5901-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5901-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c5901-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5901-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
