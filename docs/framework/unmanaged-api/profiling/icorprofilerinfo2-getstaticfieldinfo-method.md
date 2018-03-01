---
title: "ICorProfilerInfo2::GetStaticFieldInfo – metoda"
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
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8a13a07aeb90d7ad05ca83bf273fe999b9a81bd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="401ea-102">ICorProfilerInfo2::GetStaticFieldInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="401ea-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="401ea-103">Získá hodnotu, která určuje druh static, která platí pro zadané pole.</span><span class="sxs-lookup"><span data-stu-id="401ea-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="401ea-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="401ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="401ea-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="401ea-106">[v] ID třídy, ve kterém je definovaný statické pole.</span><span class="sxs-lookup"><span data-stu-id="401ea-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="401ea-107">[v] Token metadata pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="401ea-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="401ea-108">[out] Ukazatel na hodnotu [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) výčet určující, zda je zadané pole statické, a pokud ano, druh static, platí pro pole.</span><span class="sxs-lookup"><span data-stu-id="401ea-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="401ea-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="401ea-109">Remarks</span></span>  
 <span data-ttu-id="401ea-110">Tyto informace slouží k určení, které slouží k volání k získání adresy statického pole.</span><span class="sxs-lookup"><span data-stu-id="401ea-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="401ea-111">Kód profileru, měli byste zkontrolovat metadata pro statické pole zajistit, že je ve skutečnosti adresu.</span><span class="sxs-lookup"><span data-stu-id="401ea-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="401ea-112">Statické literály (konstanty) existují pouze v metadatech a nemají adresu.</span><span class="sxs-lookup"><span data-stu-id="401ea-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401ea-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="401ea-113">Requirements</span></span>  
 <span data-ttu-id="401ea-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="401ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="401ea-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="401ea-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="401ea-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="401ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="401ea-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="401ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401ea-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="401ea-118">See Also</span></span>  
 [<span data-ttu-id="401ea-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="401ea-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="401ea-120">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="401ea-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
