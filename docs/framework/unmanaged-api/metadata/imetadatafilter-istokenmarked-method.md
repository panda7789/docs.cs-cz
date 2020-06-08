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
ms.openlocfilehash: eb0ebab0f4e05d81730d5beb2b5345e319e8e274
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492535"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="15c8d-102">IMetaDataFilter::IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="15c8d-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="15c8d-103">Načte hodnotu, která označuje, jestli je zadaný token metadat označený jako zpracovaný.</span><span class="sxs-lookup"><span data-stu-id="15c8d-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15c8d-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15c8d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="15c8d-106">pro Token, který má být prověřen pro značku zpracování.</span><span class="sxs-lookup"><span data-stu-id="15c8d-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="15c8d-107">mimo Hodnota, která je `true` v případě, že byla `tk` zpracována. v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="15c8d-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c8d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15c8d-108">Requirements</span></span>  
 <span data-ttu-id="15c8d-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c8d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c8d-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="15c8d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15c8d-111">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="15c8d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15c8d-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c8d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c8d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15c8d-113">See also</span></span>

- [<span data-ttu-id="15c8d-114">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15c8d-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
