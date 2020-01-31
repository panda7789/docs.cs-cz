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
ms.openlocfilehash: 441f7743ba01884592393ce9382348fbecaeaa9d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861876"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="ddc53-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ddc53-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="ddc53-103">Vrací velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="ddc53-103">Returns the size of a specified object.</span></span> <span data-ttu-id="ddc53-104">Nahradí metodu [ICorProfilerInfo:: GetObjectSize –](icorprofilerinfo-getobjectsize-method.md) tím, že hlásí velikosti objektů, které jsou větší, než může být vyjádřeno v `ULONG`.</span><span class="sxs-lookup"><span data-stu-id="ddc53-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc53-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddc53-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddc53-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddc53-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="ddc53-107">pro ID objektu</span><span class="sxs-lookup"><span data-stu-id="ddc53-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="ddc53-108">mimo Ukazatel na velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="ddc53-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddc53-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddc53-109">Remarks</span></span>  
 <span data-ttu-id="ddc53-110">Různé objekty stejného typu mají často stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="ddc53-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="ddc53-111">Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="ddc53-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddc53-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddc53-112">Requirements</span></span>  
 <span data-ttu-id="ddc53-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddc53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddc53-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ddc53-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddc53-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ddc53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddc53-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddc53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc53-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddc53-117">See also</span></span>

- [<span data-ttu-id="ddc53-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddc53-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
