---
title: "IMetaDataEmit2::GetDeltaSaveSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.GetDeltaSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 562b7be418a4a4e335350adf5131178e406b5a07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="80b59-102">IMetaDataEmit2::GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="80b59-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="80b59-103">Získá hodnotu označující, všechny změny v velikost metadat, která je výsledkem aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="80b59-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80b59-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80b59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80b59-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="80b59-106">[v] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) hodnoty, označující úroveň přesnost potřeby.</span><span class="sxs-lookup"><span data-stu-id="80b59-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="80b59-107">Pro rozhraní .NET Framework verze 2.0 je tento parametr ignorován.</span><span class="sxs-lookup"><span data-stu-id="80b59-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="80b59-108">[out] Změna velikosti metadat.</span><span class="sxs-lookup"><span data-stu-id="80b59-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80b59-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80b59-109">Requirements</span></span>  
 <span data-ttu-id="80b59-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80b59-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80b59-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80b59-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80b59-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80b59-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80b59-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80b59-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b59-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="80b59-114">See Also</span></span>  
 [<span data-ttu-id="80b59-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80b59-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="80b59-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80b59-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
