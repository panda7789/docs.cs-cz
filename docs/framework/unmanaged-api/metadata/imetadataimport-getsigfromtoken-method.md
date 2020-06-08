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
ms.openlocfilehash: d795f90c458b7fcf1a191b2763ac5f5bb55fb438
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490884"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="c542f-102">IMetaDataImport::GetSigFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="c542f-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="c542f-103">Získá binární podpis metadat přidružených k zadanému tokenu.</span><span class="sxs-lookup"><span data-stu-id="c542f-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c542f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c542f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c542f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c542f-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="c542f-106">pro Token, pro který se má vrátit binární podpis metadat.</span><span class="sxs-lookup"><span data-stu-id="c542f-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c542f-107">mimo Ukazatel na vrácenou signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="c542f-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c542f-108">mimo Velikost v bajtech binárního podpisu metadat.</span><span class="sxs-lookup"><span data-stu-id="c542f-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c542f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c542f-109">Requirements</span></span>  
 <span data-ttu-id="c542f-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c542f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c542f-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c542f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c542f-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c542f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c542f-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c542f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c542f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c542f-114">See also</span></span>

- [<span data-ttu-id="c542f-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c542f-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c542f-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c542f-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
