---
title: "IMetaDataEmit2::SaveDeltaToMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4243840ac64a14b4f4e6c86787fdf238507635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="107ad-102">IMetaDataEmit2::SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="107ad-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="107ad-103">Uloží změny do paměti z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="107ad-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="107ad-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="107ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="107ad-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="107ad-106">[out] Adresa, kam chcete zahájit zápis delta metadat.</span><span class="sxs-lookup"><span data-stu-id="107ad-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="107ad-107">[v] Velikost změny.</span><span class="sxs-lookup"><span data-stu-id="107ad-107">[in] The size of the changes.</span></span> <span data-ttu-id="107ad-108">Použití [imetadataemit2::getdeltasavesize –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) k určení velikosti.</span><span class="sxs-lookup"><span data-stu-id="107ad-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107ad-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="107ad-109">Requirements</span></span>  
 <span data-ttu-id="107ad-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="107ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107ad-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="107ad-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="107ad-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="107ad-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="107ad-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107ad-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="107ad-114">See Also</span></span>  
 [<span data-ttu-id="107ad-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="107ad-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="107ad-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="107ad-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
