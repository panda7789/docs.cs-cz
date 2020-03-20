---
title: IMetaDataEmit::SaveToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 7db27670b72a5018a03d4614b69486f67bcef155
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175678"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="d4404-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d4404-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="d4404-103">Uloží všechna metadata v aktuálním `IStream`oboru do zadaného oboru .</span><span class="sxs-lookup"><span data-stu-id="d4404-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4404-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4404-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4404-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4404-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="d4404-106">[v] Zapisovatelný datový proud, do který chcete uložit.</span><span class="sxs-lookup"><span data-stu-id="d4404-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d4404-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="d4404-107">[in] Reserved.</span></span> <span data-ttu-id="d4404-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="d4404-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4404-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4404-109">Requirements</span></span>  
 <span data-ttu-id="d4404-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4404-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4404-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d4404-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4404-112">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4404-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4404-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4404-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4404-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4404-114">See also</span></span>

- [<span data-ttu-id="d4404-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4404-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d4404-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4404-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
