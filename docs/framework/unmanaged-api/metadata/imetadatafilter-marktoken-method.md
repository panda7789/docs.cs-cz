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
ms.openlocfilehash: 6fdd50f0de014aa68b14303e9e22924b0790fa55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786266"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="fe144-102">IMetaDataFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="fe144-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="fe144-103">Nastaví hodnotu označující, že token Zadaná metadata byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="fe144-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe144-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe144-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe144-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe144-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fe144-106">[in] Token, který chcete označit jako zpracování.</span><span class="sxs-lookup"><span data-stu-id="fe144-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe144-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe144-107">Requirements</span></span>  
 <span data-ttu-id="fe144-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe144-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe144-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe144-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe144-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe144-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe144-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe144-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe144-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe144-112">See also</span></span>

- [<span data-ttu-id="fe144-113">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe144-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
