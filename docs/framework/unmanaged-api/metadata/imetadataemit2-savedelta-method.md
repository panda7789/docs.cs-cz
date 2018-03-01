---
title: "IMetaDataEmit2::SaveDelta – metoda"
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
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31b06f014a4638fd7f947e8188730c583183f176
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="1f923-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="1f923-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="1f923-103">Uloží změny z aktuální relace upravit a pokračovat do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="1f923-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f923-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f923-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f923-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f923-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="1f923-106">[v] Název souboru, pod kterým chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="1f923-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="1f923-107">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="1f923-107">[in] Reserved.</span></span> <span data-ttu-id="1f923-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="1f923-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f923-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f923-109">Requirements</span></span>  
 <span data-ttu-id="1f923-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f923-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f923-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1f923-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f923-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f923-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f923-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f923-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f923-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f923-114">See Also</span></span>  
 [<span data-ttu-id="1f923-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f923-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="1f923-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f923-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
