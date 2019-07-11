---
title: ICorProfilerInfo4::GetObjectSize2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f72984da8f75eec35517da6ec1f8a73bc96c4609
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780807"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="e964a-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e964a-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="e964a-103">Vrátí velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e964a-103">Returns the size of a specified object.</span></span> <span data-ttu-id="e964a-104">Nahrazuje [icorprofilerinfo::getobjectsize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metody pomocí generování sestav velikosti objektů, které jsou větší, než co lze vyjádřit v `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="e964a-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e964a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e964a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e964a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e964a-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e964a-107">[in] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="e964a-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="e964a-108">[out] Ukazatel objekt velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e964a-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e964a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e964a-109">Remarks</span></span>  
 <span data-ttu-id="e964a-110">Různé objekty stejné typy často mají stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="e964a-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="e964a-111">Některé typy, například pole nebo řetězce, ale může mít jinou velikost pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="e964a-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e964a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e964a-112">Requirements</span></span>  
 <span data-ttu-id="e964a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e964a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e964a-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e964a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e964a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e964a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e964a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e964a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e964a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e964a-117">See also</span></span>

- [<span data-ttu-id="e964a-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e964a-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
