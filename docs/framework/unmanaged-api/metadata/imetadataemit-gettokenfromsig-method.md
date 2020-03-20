---
title: IMetaDataEmit::GetTokenFromSig – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: d02943f28435fc00aad8e319aa260a24cca5e307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177590"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="992e9-102">IMetaDataEmit::GetTokenFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="992e9-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="992e9-103">Získá token pro zadaný podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="992e9-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="992e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="992e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="992e9-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="992e9-106">[v] Podpis, který má být zachován a uložen.</span><span class="sxs-lookup"><span data-stu-id="992e9-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="992e9-107">[v] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="992e9-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="992e9-108">[out] Přiřazen `mdSignature` token.</span><span class="sxs-lookup"><span data-stu-id="992e9-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="992e9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="992e9-109">Requirements</span></span>  
 <span data-ttu-id="992e9-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="992e9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="992e9-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="992e9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="992e9-112">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="992e9-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="992e9-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="992e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992e9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="992e9-114">See also</span></span>

- [<span data-ttu-id="992e9-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="992e9-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="992e9-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="992e9-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
