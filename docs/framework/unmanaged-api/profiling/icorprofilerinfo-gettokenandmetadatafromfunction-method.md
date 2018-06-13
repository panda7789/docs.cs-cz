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
ms.openlocfilehash: 9bcf8919037d5b79f3819fffec02708886064b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453200"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="3bd96-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="3bd96-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="3bd96-103">Získá token metadat a instanci rozhraní metadat, které můžete použít u tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="3bd96-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bd96-104">Syntax</span></span>  
  
```  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bd96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bd96-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3bd96-106">[v] ID funkce, pro které chcete získat token metadat a metadat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3bd96-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="3bd96-107">[v] ID odkazu rozhraní metadata získat instanci.</span><span class="sxs-lookup"><span data-stu-id="3bd96-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="3bd96-108">[out] Ukazatel na adresu instanci rozhraní metadata, která můžete použít u tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="3bd96-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="3bd96-109">[out] Ukazatel na token metadata pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="3bd96-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bd96-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bd96-110">Requirements</span></span>  
 <span data-ttu-id="3bd96-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bd96-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bd96-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bd96-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bd96-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bd96-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bd96-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bd96-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd96-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bd96-115">See Also</span></span>  
 [<span data-ttu-id="3bd96-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bd96-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
