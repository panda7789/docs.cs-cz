---
title: "ICorProfilerInfo4::GetObjectSize2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetObjectSize2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0aa13a056929c9cb4f63c52f1e993f110cfca7be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="14e83-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="14e83-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="14e83-103">Vrátí velikost zadaný objekt.</span><span class="sxs-lookup"><span data-stu-id="14e83-103">Returns the size of a specified object.</span></span> <span data-ttu-id="14e83-104">Nahradí [icorprofilerinfo::getobjectsize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metoda velikosti objektů, které jsou větší než co může být vyjádřený v generování sestav `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="14e83-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14e83-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14e83-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="14e83-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="14e83-107">[v] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="14e83-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="14e83-108">[out] Ukazatel na objektu velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="14e83-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14e83-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14e83-109">Remarks</span></span>  
 <span data-ttu-id="14e83-110">Různé objekty stejné typy často mít stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="14e83-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="14e83-111">Některé typy, jako je například pole nebo řetězce, ale může mít různou velikost pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="14e83-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14e83-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14e83-112">Requirements</span></span>  
 <span data-ttu-id="14e83-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14e83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14e83-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14e83-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14e83-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14e83-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14e83-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14e83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e83-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="14e83-117">See Also</span></span>  
 [<span data-ttu-id="14e83-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14e83-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
