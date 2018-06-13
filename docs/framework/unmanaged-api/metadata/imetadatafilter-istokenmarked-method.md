---
title: IMetaDataFilter::IsTokenMarked – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bf5149e8e42a810a6a490767638b374f66b5679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445861"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="c62fe-102">IMetaDataFilter::IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="c62fe-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="c62fe-103">Získá hodnotu označující, zda zadaná metadata token byla označena jako zpracovaná.</span><span class="sxs-lookup"><span data-stu-id="c62fe-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c62fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c62fe-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c62fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c62fe-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c62fe-106">[v] Token k prozkoumání pro zpracování značky.</span><span class="sxs-lookup"><span data-stu-id="c62fe-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="c62fe-107">[out] Hodnotu, která je `true` Pokud `tk` byl zpracován; jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="c62fe-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c62fe-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c62fe-108">Requirements</span></span>  
 <span data-ttu-id="c62fe-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c62fe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c62fe-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c62fe-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c62fe-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c62fe-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c62fe-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c62fe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c62fe-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c62fe-113">See Also</span></span>  
 [<span data-ttu-id="c62fe-114">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c62fe-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
