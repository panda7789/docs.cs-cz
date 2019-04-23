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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 179cfc5c0725934e21d7b89a2f8d4c934b049f78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106051"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="f11dd-102">IMetaDataEmit::Merge – metoda</span><span class="sxs-lookup"><span data-stu-id="f11dd-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="f11dd-103">Přidá do seznamu oborů, která se má sloučit zadané importované oboru.</span><span class="sxs-lookup"><span data-stu-id="f11dd-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11dd-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f11dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f11dd-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="f11dd-106">[in] Ukazatel [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objekt, který identifikuje importované oboru ke sloučení.</span><span class="sxs-lookup"><span data-stu-id="f11dd-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="f11dd-107">[in] Ukazatel [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objekt, který určuje, token přemapovat.</span><span class="sxs-lookup"><span data-stu-id="f11dd-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="f11dd-108">[in] Ukazatel [IUnknown](/cpp/atl/iunknown) objekt, který určuje chyby.</span><span class="sxs-lookup"><span data-stu-id="f11dd-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f11dd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f11dd-109">Remarks</span></span>  
 <span data-ttu-id="f11dd-110">Volání [imetadataemit::mergeend –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) k aktivaci spojení metadat do jednoho oboru.</span><span class="sxs-lookup"><span data-stu-id="f11dd-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11dd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f11dd-111">Requirements</span></span>  
 <span data-ttu-id="f11dd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f11dd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11dd-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f11dd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f11dd-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f11dd-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f11dd-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11dd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11dd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f11dd-116">See also</span></span>

- [<span data-ttu-id="f11dd-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11dd-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f11dd-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f11dd-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
