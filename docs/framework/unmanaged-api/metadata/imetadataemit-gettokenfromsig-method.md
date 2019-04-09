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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 242618fb2a5ab748132baf68e24240d1ffaf2301
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139838"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="fc3c6-102">IMetaDataEmit::GetTokenFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="fc3c6-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="fc3c6-103">Získá token pro Zadaná metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc3c6-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc3c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc3c6-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="fc3c6-106">[in] Podpis trvale uložila a uložené.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="fc3c6-107">[in] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="fc3c6-108">[out] `mdSignature` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="fc3c6-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3c6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc3c6-109">Requirements</span></span>  
 <span data-ttu-id="fc3c6-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc3c6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3c6-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc3c6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc3c6-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc3c6-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fc3c6-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fc3c6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc3c6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc3c6-114">See also</span></span>

- [<span data-ttu-id="fc3c6-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc3c6-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fc3c6-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc3c6-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
