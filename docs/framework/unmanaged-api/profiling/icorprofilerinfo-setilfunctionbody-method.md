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
ms.openlocfilehash: d10bb7033688efce9488078d2ef605e2a29382f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221411"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="54d2a-102">ICorProfilerInfo::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="54d2a-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="54d2a-103">Nahrazuje tělo zadanou funkci v zadaném modulu.</span><span class="sxs-lookup"><span data-stu-id="54d2a-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54d2a-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54d2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54d2a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="54d2a-106">[in] ID modulu, ve kterém se funkce nachází.</span><span class="sxs-lookup"><span data-stu-id="54d2a-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="54d2a-107">[in] Token pro které se mají nahradit tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="54d2a-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="54d2a-108">[in] Nové záhlaví pro funkci.</span><span class="sxs-lookup"><span data-stu-id="54d2a-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54d2a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54d2a-109">Remarks</span></span>  
 <span data-ttu-id="54d2a-110">`SetILFunctionBody` Metoda nahrazuje relativní virtuální adresu funkce v metadatech tak, aby odkazuje na nové tělo funkce a upraví interních datových struktur podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="54d2a-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="54d2a-111">`SetILFunctionBody` Metodu lze volat pouze funkce, které nikdy byl zkompilován kompilátorem just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="54d2a-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="54d2a-112">Použití [icorprofilerinfo::getilfunctionbodyallocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) metoda k přidělení místa pro nové metody k zajištění, že vyrovnávací paměť je kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="54d2a-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54d2a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54d2a-113">Requirements</span></span>  
 <span data-ttu-id="54d2a-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54d2a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54d2a-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54d2a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54d2a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54d2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54d2a-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54d2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d2a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54d2a-118">See also</span></span>

- [<span data-ttu-id="54d2a-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54d2a-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
