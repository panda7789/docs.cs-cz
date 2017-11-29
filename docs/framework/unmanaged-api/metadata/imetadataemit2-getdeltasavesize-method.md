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
ms.openlocfilehash: 0a1b3aec06d6593257c82d6e3c08d6a8e2430691
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="d0c6e-102">IMetaDataEmit2::GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d0c6e-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="d0c6e-103">Získá hodnotu označující, všechny změny v velikost metadat, která je výsledkem aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="d0c6e-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0c6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0c6e-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0c6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0c6e-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="d0c6e-106">[v] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) hodnoty, označující úroveň přesnost potřeby.</span><span class="sxs-lookup"><span data-stu-id="d0c6e-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="d0c6e-107">Pro rozhraní .NET Framework verze 2.0 je tento parametr ignorován.</span><span class="sxs-lookup"><span data-stu-id="d0c6e-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="d0c6e-108">[out] Změna velikosti metadat.</span><span class="sxs-lookup"><span data-stu-id="d0c6e-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0c6e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0c6e-109">Requirements</span></span>  
 <span data-ttu-id="d0c6e-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0c6e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0c6e-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0c6e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0c6e-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0c6e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0c6e-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0c6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c6e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0c6e-114">See Also</span></span>  
 [<span data-ttu-id="d0c6e-115">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0c6e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="d0c6e-116">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0c6e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
