---
title: ICorProfilerInfo::GetClassFromObject – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 460162f0fbc9993635d1bce0c5b130358ced4fa7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448145"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="e7d95-102">ICorProfilerInfo::GetClassFromObject – metoda</span><span class="sxs-lookup"><span data-stu-id="e7d95-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="e7d95-103">Gets the `ClassID` of an object, given its `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="e7d95-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7d95-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7d95-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e7d95-106">[in] The ID of the object for which to get the `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="e7d95-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="e7d95-107">[out] A pointer to the returned `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="e7d95-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7d95-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7d95-108">Remarks</span></span>  
 <span data-ttu-id="e7d95-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span><span class="sxs-lookup"><span data-stu-id="e7d95-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d95-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7d95-110">Requirements</span></span>  
 <span data-ttu-id="e7d95-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d95-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d95-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7d95-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7d95-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7d95-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d95-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d95-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d95-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7d95-115">See also</span></span>

- [<span data-ttu-id="e7d95-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7d95-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
