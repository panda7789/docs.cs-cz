---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb81972a7f52889d10a59cd5cd9ea0e8e1e3e571
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492878"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="a01c9-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="a01c9-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="a01c9-103">Získá token metadat a instanci rozhraní metadata, která se dá použít pro token pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="a01c9-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a01c9-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a01c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a01c9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a01c9-106">[in] ID funkce, pro které chcete-li získat token metadat a interface metadat.</span><span class="sxs-lookup"><span data-stu-id="a01c9-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="a01c9-107">[in] Referenční ID rozhraní metadata k získání instance.</span><span class="sxs-lookup"><span data-stu-id="a01c9-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="a01c9-108">[out] Ukazatel na adresu rozhraní instance metadata a dá se použít pro token pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="a01c9-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="a01c9-109">[out] Ukazatel na token metadata pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="a01c9-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01c9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a01c9-110">Requirements</span></span>  
 <span data-ttu-id="a01c9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a01c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01c9-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a01c9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a01c9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a01c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a01c9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01c9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a01c9-115">See also</span></span>
- [<span data-ttu-id="a01c9-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a01c9-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
