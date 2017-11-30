---
title: "ICorProfilerInfo::GetClassFromObject – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromObject
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 706118a197677ec97672cca36f5bcf6421a1c328
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="c14fd-102">ICorProfilerInfo::GetClassFromObject – metoda</span><span class="sxs-lookup"><span data-stu-id="c14fd-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="c14fd-103">Získá `ClassID` objektu zadané jeho `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="c14fd-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c14fd-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c14fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c14fd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="c14fd-106">[v] ID objektu, pro které chcete získat `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="c14fd-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="c14fd-107">[out] Ukazatel na vrácený `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="c14fd-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c14fd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c14fd-108">Remarks</span></span>  
 <span data-ttu-id="c14fd-109">Null `pClassId` znamená, že `objectId` má typ, který je uvolnění.</span><span class="sxs-lookup"><span data-stu-id="c14fd-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c14fd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c14fd-110">Requirements</span></span>  
 <span data-ttu-id="c14fd-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c14fd-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c14fd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c14fd-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c14fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c14fd-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c14fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14fd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c14fd-115">See Also</span></span>  
 [<span data-ttu-id="c14fd-116">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c14fd-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
