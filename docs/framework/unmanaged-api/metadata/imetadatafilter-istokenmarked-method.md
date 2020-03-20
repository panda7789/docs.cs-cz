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
ms.openlocfilehash: 47377e892aaf2bdd96a297630c47fe52215b0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177385"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="654aa-102">IMetaDataFilter::IsTokenMarked – metoda</span><span class="sxs-lookup"><span data-stu-id="654aa-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="654aa-103">Získá hodnotu označující, zda byl zadaný token metadat označen jako zpracovaný.</span><span class="sxs-lookup"><span data-stu-id="654aa-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="654aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="654aa-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="654aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="654aa-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="654aa-106">[v] Token zkoumat pro značku zpracování.</span><span class="sxs-lookup"><span data-stu-id="654aa-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="654aa-107">[out] Hodnota, která `true` `tk` je- li byla zpracována; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="654aa-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="654aa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="654aa-108">Requirements</span></span>  
 <span data-ttu-id="654aa-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="654aa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="654aa-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="654aa-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="654aa-111">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="654aa-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="654aa-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="654aa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654aa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="654aa-113">See also</span></span>

- [<span data-ttu-id="654aa-114">IMetaDataFilter – rozhraní</span><span class="sxs-lookup"><span data-stu-id="654aa-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
