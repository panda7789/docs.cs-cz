---
title: "IMetaDataError::OnError – metoda"
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
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6e136f3fd76b9eb2be1e49a48316dc65c481fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="bb53b-102">IMetaDataError::OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="bb53b-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="bb53b-103">Poskytuje oznámení chyb, ke kterým došlo během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="bb53b-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb53b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb53b-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb53b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb53b-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="bb53b-106">[v] Hodnota chyby HRESULT vrácená volání metody.</span><span class="sxs-lookup"><span data-stu-id="bb53b-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="bb53b-107">[v] Token metadata objektu kód, který slučování když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="bb53b-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb53b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb53b-108">Requirements</span></span>  
 <span data-ttu-id="bb53b-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb53b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb53b-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb53b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb53b-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb53b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb53b-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb53b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb53b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb53b-113">See Also</span></span>  
 [<span data-ttu-id="bb53b-114">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb53b-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
