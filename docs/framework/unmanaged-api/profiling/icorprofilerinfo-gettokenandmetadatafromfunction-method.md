---
title: "ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda"
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
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 33522d55383b1137d8591c74c988903655eba5f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="eb73f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="eb73f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="eb73f-103">Získá token metadat a instanci rozhraní metadat, které můžete použít u tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="eb73f-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb73f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb73f-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb73f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb73f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="eb73f-106">[v] ID funkce, pro které chcete získat token metadat a metadat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb73f-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="eb73f-107">[v] ID odkazu rozhraní metadata získat instanci.</span><span class="sxs-lookup"><span data-stu-id="eb73f-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="eb73f-108">[out] Ukazatel na adresu instanci rozhraní metadata, která můžete použít u tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="eb73f-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="eb73f-109">[out] Ukazatel na token metadata pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="eb73f-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb73f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb73f-110">Requirements</span></span>  
 <span data-ttu-id="eb73f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb73f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb73f-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb73f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb73f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb73f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb73f-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb73f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb73f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb73f-115">See Also</span></span>  
 [<span data-ttu-id="eb73f-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb73f-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
