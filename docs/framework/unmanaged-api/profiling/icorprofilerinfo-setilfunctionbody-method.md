---
title: ICorProfilerInfo::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 886bb706be30481c082012bf057a001f37903b16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461653"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="45e8b-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="45e8b-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="45e8b-103">Nahradí text zadaná funkce v zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="45e8b-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45e8b-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45e8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45e8b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45e8b-106">[v] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="45e8b-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="45e8b-107">[v] Token pro kterou chcete nahradit tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="45e8b-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="45e8b-108">[v] Nové záhlaví funkce.</span><span class="sxs-lookup"><span data-stu-id="45e8b-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e8b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45e8b-109">Remarks</span></span>  
 <span data-ttu-id="45e8b-110">`SetILFunctionBody` Metoda nahrazuje relativní virtuální adresy funkce v metadatech tak, aby odkazoval na nový tělo funkce a upraví interních datových struktur podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="45e8b-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="45e8b-111">`SetILFunctionBody` Metodu lze volat pouze funkce, které nikdy sestavili jsme kompilátorem v běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="45e8b-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="45e8b-112">Použití [icorprofilerinfo::getilfunctionbodyallocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metoda k přidělení místa pro nová metoda pro zajištění, že vyrovnávací paměť je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="45e8b-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e8b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45e8b-113">Requirements</span></span>  
 <span data-ttu-id="45e8b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e8b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e8b-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45e8b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45e8b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45e8b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e8b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e8b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e8b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="45e8b-118">See Also</span></span>  
 [<span data-ttu-id="45e8b-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45e8b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
