---
title: "ICorProfilerInfo::GetFunctionInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17512077ef7a8ca45fa76c00f93612015948d083
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="3cebe-102">ICorProfilerInfo::GetFunctionInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="3cebe-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="3cebe-103">Získá nadřazené třídy a metadata token pro zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="3cebe-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cebe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cebe-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cebe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cebe-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3cebe-106">[v] ID funkce, pro které chcete získat token nadřazené třídy a metadata.</span><span class="sxs-lookup"><span data-stu-id="3cebe-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="3cebe-107">[out] Ukazatel na nadřazené třídy funkce.</span><span class="sxs-lookup"><span data-stu-id="3cebe-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="3cebe-108">[out] Ukazatel na modul, ve kterém je definovaný funkce nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="3cebe-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="3cebe-109">[out] Ukazatel na token metadata pro funkci.</span><span class="sxs-lookup"><span data-stu-id="3cebe-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cebe-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cebe-110">Remarks</span></span>  
 <span data-ttu-id="3cebe-111">Můžete volat kód profileru [icorprofilerinfo::getmodulemetadata –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) k získání metadat rozhraní pro daného modulu.</span><span class="sxs-lookup"><span data-stu-id="3cebe-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="3cebe-112">Metadata token, který je vrácen do umístění odkazuje `pToken` pak lze získat přístup k metadatům pro funkci.</span><span class="sxs-lookup"><span data-stu-id="3cebe-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="3cebe-113">`ClassID` Funkce na obecné třídy nemusí být dosažitelný bez další kontextové informace o použití funkce.</span><span class="sxs-lookup"><span data-stu-id="3cebe-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="3cebe-114">V takovém případě `pClassId` bude 0.</span><span class="sxs-lookup"><span data-stu-id="3cebe-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="3cebe-115">Profileru kód by měl používat [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou COR_PRF_FRAME_INFO zajistit další kontext.</span><span class="sxs-lookup"><span data-stu-id="3cebe-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cebe-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cebe-116">Requirements</span></span>  
 <span data-ttu-id="3cebe-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cebe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cebe-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cebe-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cebe-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cebe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cebe-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cebe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cebe-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cebe-121">See Also</span></span>  
 [<span data-ttu-id="3cebe-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cebe-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
