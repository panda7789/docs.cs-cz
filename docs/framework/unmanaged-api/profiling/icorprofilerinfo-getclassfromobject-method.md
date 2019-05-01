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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81afb9b40269b04a59c54636c7e88c1f67189593
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041708"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="7c595-102">ICorProfilerInfo::GetClassFromObject – metoda</span><span class="sxs-lookup"><span data-stu-id="7c595-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="7c595-103">Získá `ClassID` objektu, dle jeho `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="7c595-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c595-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c595-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c595-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c595-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7c595-106">[in] ID objektu, pro který má být získána `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="7c595-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="7c595-107">[out] Ukazatel na vrácenou `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="7c595-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c595-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c595-108">Remarks</span></span>  
 <span data-ttu-id="7c595-109">S hodnotou null `pClassId` znamená, že `objectId` má typ, který je uvolnění.</span><span class="sxs-lookup"><span data-stu-id="7c595-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c595-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c595-110">Requirements</span></span>  
 <span data-ttu-id="7c595-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c595-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c595-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7c595-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7c595-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c595-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c595-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c595-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c595-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c595-115">See also</span></span>

- [<span data-ttu-id="7c595-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c595-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
