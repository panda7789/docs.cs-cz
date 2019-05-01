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
ms.openlocfilehash: 15829e08a755b91ff91ca939b92a5a87bd377e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000672"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="97d82-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="97d82-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="97d82-103">Vrátí velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="97d82-103">Returns the size of a specified object.</span></span> <span data-ttu-id="97d82-104">Nahrazuje [icorprofilerinfo::getobjectsize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) metody pomocí generování sestav velikosti objektů, které jsou větší, než co lze vyjádřit v `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="97d82-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d82-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97d82-105">Syntax</span></span>  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d82-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d82-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="97d82-107">[in] ID objektu.</span><span class="sxs-lookup"><span data-stu-id="97d82-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="97d82-108">[out] Ukazatel objekt velikost v bajtech.</span><span class="sxs-lookup"><span data-stu-id="97d82-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d82-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97d82-109">Remarks</span></span>  
 <span data-ttu-id="97d82-110">Různé objekty stejné typy často mají stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="97d82-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="97d82-111">Některé typy, například pole nebo řetězce, ale může mít jinou velikost pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="97d82-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d82-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97d82-112">Requirements</span></span>  
 <span data-ttu-id="97d82-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d82-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97d82-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97d82-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d82-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d82-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d82-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97d82-117">See also</span></span>

- [<span data-ttu-id="97d82-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97d82-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
