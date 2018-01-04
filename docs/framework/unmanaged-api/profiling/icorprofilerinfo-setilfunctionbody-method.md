---
title: "ICorProfilerInfo::SetILFunctionBody – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c44fa89ba66a306792f1ffed162447a6305a0347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="c072d-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="c072d-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="c072d-103">Nahradí text zadaná funkce v zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="c072d-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c072d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c072d-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c072d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c072d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c072d-106">[v] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="c072d-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="c072d-107">[v] Token pro kterou chcete nahradit tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="c072d-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="c072d-108">[v] Nové záhlaví funkce.</span><span class="sxs-lookup"><span data-stu-id="c072d-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c072d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c072d-109">Remarks</span></span>  
 <span data-ttu-id="c072d-110">`SetILFunctionBody` Metoda nahrazuje relativní virtuální adresy funkce v metadatech tak, aby odkazoval na nový tělo funkce a upraví interních datových struktur podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="c072d-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="c072d-111">`SetILFunctionBody` Metodu lze volat pouze funkce, které nikdy sestavili jsme kompilátorem v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="c072d-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="c072d-112">Použití [icorprofilerinfo::getilfunctionbodyallocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metoda k přidělení místa pro nová metoda pro zajištění, že vyrovnávací paměť je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="c072d-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c072d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c072d-113">Requirements</span></span>  
 <span data-ttu-id="c072d-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c072d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c072d-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c072d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c072d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c072d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c072d-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c072d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c072d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c072d-118">See Also</span></span>  
 [<span data-ttu-id="c072d-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c072d-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
