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
ms.openlocfilehash: b3e14230888e9bf846879d5728c2b20883fb8d53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438737"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="49c86-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="49c86-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="49c86-103">Získá token metadat a instanci rozhraní metadat, kterou lze použít proti tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="49c86-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49c86-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49c86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49c86-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="49c86-106">pro ID funkce, pro kterou se má získat token metadat a rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="49c86-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="49c86-107">pro Referenční ID rozhraní metadat, pro které se má získat instance</span><span class="sxs-lookup"><span data-stu-id="49c86-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="49c86-108">mimo Ukazatel na adresu instance rozhraní metadat, kterou lze použít proti tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="49c86-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="49c86-109">mimo Ukazatel na token metadat pro určenou funkci.</span><span class="sxs-lookup"><span data-stu-id="49c86-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c86-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49c86-110">Requirements</span></span>  
 <span data-ttu-id="49c86-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49c86-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c86-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="49c86-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49c86-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49c86-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c86-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49c86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c86-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49c86-115">See also</span></span>

- [<span data-ttu-id="49c86-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49c86-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
