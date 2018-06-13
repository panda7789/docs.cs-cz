---
title: IHostFilter::MarkToken – metoda
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444561"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="e5dfc-102">IHostFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e5dfc-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="e5dfc-103">Označuje, že zadaná metadata token budou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="e5dfc-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5dfc-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5dfc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5dfc-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e5dfc-106">[v] Token metadata mají být zpracovány.</span><span class="sxs-lookup"><span data-stu-id="e5dfc-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5dfc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5dfc-107">Remarks</span></span>  
 <span data-ttu-id="e5dfc-108">Obvykle je vhodné token mají být zpracovány, pokud se nachází v oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="e5dfc-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="e5dfc-109">`MarkToken` Metodě se předává metadata stroji prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="e5dfc-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5dfc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5dfc-110">Requirements</span></span>  
 <span data-ttu-id="e5dfc-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5dfc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dfc-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5dfc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5dfc-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5dfc-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5dfc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dfc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dfc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5dfc-115">See Also</span></span>  
 [<span data-ttu-id="e5dfc-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="e5dfc-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="e5dfc-117">IHostFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5dfc-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
