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
ms.openlocfilehash: d924dbf21a0f0b046c8d8f8f294e91bc5ff6c015
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869408"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="6766f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="6766f-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="6766f-103">Získá token metadat a instanci rozhraní metadat, kterou lze použít proti tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="6766f-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6766f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6766f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6766f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6766f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6766f-106">pro ID funkce, pro kterou se má získat token metadat a rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="6766f-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="6766f-107">pro Referenční ID rozhraní metadat, pro které se má získat instance</span><span class="sxs-lookup"><span data-stu-id="6766f-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="6766f-108">mimo Ukazatel na adresu instance rozhraní metadat, kterou lze použít proti tokenu pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="6766f-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="6766f-109">mimo Ukazatel na token metadat pro určenou funkci.</span><span class="sxs-lookup"><span data-stu-id="6766f-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6766f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6766f-110">Requirements</span></span>  
 <span data-ttu-id="6766f-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6766f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6766f-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6766f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6766f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6766f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6766f-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6766f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6766f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6766f-115">See also</span></span>

- [<span data-ttu-id="6766f-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6766f-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
