---
title: IMetaDataEmit::Merge – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175704"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="73685-102">IMetaDataEmit::Merge – metoda</span><span class="sxs-lookup"><span data-stu-id="73685-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="73685-103">Přidá zadaný importovaný obor do seznamu oborů, které mají být sloučeny.</span><span class="sxs-lookup"><span data-stu-id="73685-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73685-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73685-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73685-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73685-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="73685-106">[v] Ukazatel na objekt [IMetaDataImport,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) který identifikuje importovaný obor, který má být sloučen.</span><span class="sxs-lookup"><span data-stu-id="73685-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="73685-107">[v] Ukazatel na objekt [IMapToken,](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) který určuje znovu namapovat token.</span><span class="sxs-lookup"><span data-stu-id="73685-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="73685-108">[v] Ukazatel na objekt [IUnknown,](/cpp/atl/iunknown) který určuje chyby.</span><span class="sxs-lookup"><span data-stu-id="73685-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73685-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73685-109">Remarks</span></span>  
 <span data-ttu-id="73685-110">Volání [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) pro aktivaci sloučení metadat do jednoho oboru.</span><span class="sxs-lookup"><span data-stu-id="73685-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73685-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73685-111">Requirements</span></span>  
 <span data-ttu-id="73685-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73685-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73685-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="73685-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73685-114">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73685-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73685-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73685-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73685-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="73685-116">See also</span></span>

- [<span data-ttu-id="73685-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73685-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="73685-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73685-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
