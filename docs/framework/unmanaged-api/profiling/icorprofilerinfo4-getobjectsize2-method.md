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
ms.openlocfilehash: fdfba34f35e40b2a50dbc4edc5b6b6c45f17194f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442871"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="d3cbe-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d3cbe-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="d3cbe-103">Vrací velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="d3cbe-103">Returns the size of a specified object.</span></span> <span data-ttu-id="d3cbe-104">Nahradí metodu [ICorProfilerInfo:: GetObjectSize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) tím, že hlásí velikosti objektů, které jsou větší, než může být vyjádřeno v `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="d3cbe-104">Replaces the [ICorProfilerInfo::GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3cbe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3cbe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3cbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3cbe-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="d3cbe-107">pro ID objektu</span><span class="sxs-lookup"><span data-stu-id="d3cbe-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="d3cbe-108">mimo Ukazatel na velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d3cbe-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3cbe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3cbe-109">Remarks</span></span>  
 <span data-ttu-id="d3cbe-110">Různé objekty stejného typu mají často stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="d3cbe-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="d3cbe-111">Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="d3cbe-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3cbe-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3cbe-112">Requirements</span></span>  
 <span data-ttu-id="d3cbe-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3cbe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3cbe-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d3cbe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3cbe-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d3cbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3cbe-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3cbe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3cbe-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3cbe-117">See also</span></span>

- [<span data-ttu-id="d3cbe-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3cbe-118">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
