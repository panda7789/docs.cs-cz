---
title: IMetaDataImport::GetSigFromToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 292ab8684f20c7ec5dcb87784c0ffff7416e8880
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476344"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="3647b-102">IMetaDataImport::GetSigFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="3647b-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="3647b-103">Získá metadata binární podpis přidružené k zadaným tokenu.</span><span class="sxs-lookup"><span data-stu-id="3647b-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3647b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3647b-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3647b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3647b-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="3647b-106">[in] Token se vraťte podpis binárního metadat pro.</span><span class="sxs-lookup"><span data-stu-id="3647b-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="3647b-107">[out] Ukazatel na podpis vrácených metadat.</span><span class="sxs-lookup"><span data-stu-id="3647b-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="3647b-108">[out] Velikost v bajtech binárního metadat podpisu.</span><span class="sxs-lookup"><span data-stu-id="3647b-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3647b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3647b-109">Requirements</span></span>  
 <span data-ttu-id="3647b-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3647b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3647b-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3647b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3647b-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3647b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3647b-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3647b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3647b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3647b-114">See also</span></span>
- [<span data-ttu-id="3647b-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3647b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3647b-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3647b-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
