---
title: "IMetaDataFilter::MarkToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb40d7674caae119b39f49b0c1024c7500bc892a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="00e64-102">IMetaDataFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="00e64-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="00e64-103">Nastaví hodnotu, která určuje, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="00e64-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00e64-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00e64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00e64-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="00e64-106">[v] Token, který má označit jako zpracovaná.</span><span class="sxs-lookup"><span data-stu-id="00e64-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00e64-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00e64-107">Requirements</span></span>  
 <span data-ttu-id="00e64-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e64-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e64-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00e64-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00e64-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00e64-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00e64-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e64-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e64-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="00e64-112">See Also</span></span>  
 [<span data-ttu-id="00e64-113">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00e64-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
