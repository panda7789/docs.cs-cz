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
ms.openlocfilehash: 97f184bae4628f2aa357644188594396468671ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444149"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="832fc-102">IMetaDataFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="832fc-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="832fc-103">Nastaví hodnotu, která určuje, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="832fc-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="832fc-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="832fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="832fc-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="832fc-106">[v] Token, který má označit jako zpracovaná.</span><span class="sxs-lookup"><span data-stu-id="832fc-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="832fc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="832fc-107">Requirements</span></span>  
 <span data-ttu-id="832fc-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="832fc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="832fc-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="832fc-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="832fc-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="832fc-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="832fc-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="832fc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832fc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="832fc-112">See Also</span></span>  
 [<span data-ttu-id="832fc-113">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="832fc-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
