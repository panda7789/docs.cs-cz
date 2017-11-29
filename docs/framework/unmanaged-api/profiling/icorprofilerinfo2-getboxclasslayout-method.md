---
title: "ICorProfilerInfo2::GetBoxClassLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetBoxClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c11013781a4fc8f627dac97894ff9ef02bfda51c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="cb33c-102">ICorProfilerInfo2::GetBoxClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="cb33c-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="cb33c-103">Získá informace o tom, kde nachází typ zadané hodnoty při je zabalená.</span><span class="sxs-lookup"><span data-stu-id="cb33c-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb33c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb33c-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb33c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb33c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cb33c-106">[v] ID třídy, která popisuje typ hodnoty, který je zabalená.</span><span class="sxs-lookup"><span data-stu-id="cb33c-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="cb33c-107">[out] Celé číslo, které je posun vzhledem k zabalené objekt ukazatel ID typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cb33c-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb33c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb33c-108">Remarks</span></span>  
 <span data-ttu-id="cb33c-109">`pBufferOffset` Hodnota je umístění typ hodnoty v rámci pole.</span><span class="sxs-lookup"><span data-stu-id="cb33c-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="cb33c-110">Po `pBufferOffset` se použije na objekt zabalené rozložení třída typ hodnoty lze interpretovat hodnota objektu.</span><span class="sxs-lookup"><span data-stu-id="cb33c-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb33c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb33c-111">Requirements</span></span>  
 <span data-ttu-id="cb33c-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb33c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb33c-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb33c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb33c-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb33c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb33c-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb33c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb33c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb33c-116">See Also</span></span>  
 [<span data-ttu-id="cb33c-117">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb33c-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="cb33c-118">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb33c-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
