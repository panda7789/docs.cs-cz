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
ms.openlocfilehash: b605419a291f7bee76ecad7e07be9a7a989f9fe9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496006"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="05116-102">ICorProfilerInfo4::GetObjectSize2 – metoda</span><span class="sxs-lookup"><span data-stu-id="05116-102">ICorProfilerInfo4::GetObjectSize2 Method</span></span>
<span data-ttu-id="05116-103">Vrací velikost zadaného objektu.</span><span class="sxs-lookup"><span data-stu-id="05116-103">Returns the size of a specified object.</span></span> <span data-ttu-id="05116-104">Nahradí metodu [ICorProfilerInfo:: GetObjectSize –](icorprofilerinfo-getobjectsize-method.md) sestavou velikosti objektů, které jsou větší, než může být vyjádřeno v `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="05116-104">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05116-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05116-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05116-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="05116-106">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="05116-107">pro ID objektu</span><span class="sxs-lookup"><span data-stu-id="05116-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="05116-108">mimo Ukazatel na velikost objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="05116-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05116-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05116-109">Remarks</span></span>  
 <span data-ttu-id="05116-110">Různé objekty stejného typu mají často stejnou velikost.</span><span class="sxs-lookup"><span data-stu-id="05116-110">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="05116-111">Některé typy, například pole nebo řetězce, mohou mít různé velikosti pro každý objekt.</span><span class="sxs-lookup"><span data-stu-id="05116-111">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05116-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05116-112">Requirements</span></span>  
 <span data-ttu-id="05116-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05116-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05116-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05116-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05116-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05116-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05116-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05116-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05116-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05116-117">See also</span></span>

- [<span data-ttu-id="05116-118">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05116-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
