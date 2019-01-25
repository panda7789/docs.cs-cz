---
title: IMetaDataFilter::MarkToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0c1edf5eb01c3cb94633b5185ef5b21bd9716e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557851"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="6230e-102">IMetaDataFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="6230e-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="6230e-103">Nastaví hodnotu označující, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="6230e-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6230e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6230e-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6230e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6230e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6230e-106">[in] Token, který chcete označit jako zpracování.</span><span class="sxs-lookup"><span data-stu-id="6230e-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6230e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6230e-107">Requirements</span></span>  
 <span data-ttu-id="6230e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6230e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6230e-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6230e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6230e-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6230e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6230e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6230e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6230e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6230e-112">See also</span></span>
- [<span data-ttu-id="6230e-113">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6230e-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
