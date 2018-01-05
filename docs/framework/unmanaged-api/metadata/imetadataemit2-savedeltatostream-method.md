---
title: "IMetaDataEmit2::SaveDeltaToStream – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcfd90da200e04e5834b21ea84a3a84acc5b732d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="198c2-102">IMetaDataEmit2::SaveDeltaToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="198c2-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="198c2-103">Uloží změny do zadaného datového proudu z aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="198c2-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="198c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="198c2-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="198c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="198c2-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="198c2-106">[v] Ukazatel rozhraní s možností zápisu datového proudu, do které chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="198c2-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="198c2-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="198c2-107">[in] Reserved.</span></span> <span data-ttu-id="198c2-108">Tato hodnota musí být nula.</span><span class="sxs-lookup"><span data-stu-id="198c2-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="198c2-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="198c2-109">Requirements</span></span>  
 <span data-ttu-id="198c2-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="198c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="198c2-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="198c2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="198c2-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="198c2-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="198c2-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="198c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="198c2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="198c2-114">See Also</span></span>  
 [<span data-ttu-id="198c2-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="198c2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="198c2-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="198c2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
