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
ms.openlocfilehash: f486ffd1206dd30fa29d3f07c8c5b738cc207db0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745868"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="4815c-102">IHostFilter::MarkToken – metoda</span><span class="sxs-lookup"><span data-stu-id="4815c-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="4815c-103">Označuje, že se zpracuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="4815c-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4815c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4815c-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4815c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4815c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4815c-106">[in] Tokenu metadat na zpracování.</span><span class="sxs-lookup"><span data-stu-id="4815c-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4815c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4815c-107">Remarks</span></span>  
 <span data-ttu-id="4815c-108">Obvykle je vhodné token ke zpracování, pokud se nachází v oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="4815c-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="4815c-109">`MarkToken` Metoda předána do modulu metadat prostřednictvím [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4815c-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4815c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4815c-110">Requirements</span></span>  
 <span data-ttu-id="4815c-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4815c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4815c-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4815c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4815c-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4815c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4815c-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4815c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4815c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4815c-115">See also</span></span>

- [<span data-ttu-id="4815c-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="4815c-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="4815c-117">IHostFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4815c-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
