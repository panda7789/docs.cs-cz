---
title: "IMetaDataEmit::Merge – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f05f2e39365b021e902b2bdaa41cda481b5af8b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="54b2f-102">IMetaDataEmit::Merge – metoda</span><span class="sxs-lookup"><span data-stu-id="54b2f-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="54b2f-103">Zadaný obor importované přidá do seznamu oborů, který se má sloučit.</span><span class="sxs-lookup"><span data-stu-id="54b2f-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54b2f-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54b2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54b2f-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="54b2f-106">[v] Ukazatel na [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objekt, který identifikuje importované oboru, který se má sloučit.</span><span class="sxs-lookup"><span data-stu-id="54b2f-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="54b2f-107">[v] Ukazatel na [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) objekt, který určuje, tokenu znovu namapovat.</span><span class="sxs-lookup"><span data-stu-id="54b2f-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="54b2f-108">[v] Ukazatel na <!--<<!--zzxref:IUnknown --> `IUnknown` >-->  `IUnknown` objekt, který určuje chyby.</span><span class="sxs-lookup"><span data-stu-id="54b2f-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54b2f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54b2f-109">Remarks</span></span>  
 <span data-ttu-id="54b2f-110">Volání [imetadataemit::mergeend –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) k aktivaci fúze metadat do jednoho oboru.</span><span class="sxs-lookup"><span data-stu-id="54b2f-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54b2f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54b2f-111">Requirements</span></span>  
 <span data-ttu-id="54b2f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b2f-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54b2f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54b2f-114">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54b2f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54b2f-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54b2f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b2f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="54b2f-116">See Also</span></span>  
 [<span data-ttu-id="54b2f-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54b2f-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="54b2f-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54b2f-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
