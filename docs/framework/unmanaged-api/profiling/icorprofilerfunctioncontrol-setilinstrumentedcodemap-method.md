---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: 11ce2fdccbf24fd688376cc3256f6db79a7cc352
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447855"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="6a8fa-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="6a8fa-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="6a8fa-103">Nastaví mapu kódu pro určenou funkci pomocí zadaných položek mapování Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="6a8fa-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a8fa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a8fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a8fa-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="6a8fa-106">pro Počet položek v mapě.</span><span class="sxs-lookup"><span data-stu-id="6a8fa-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="6a8fa-107">pro Pole přidělené volajícím položkám COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="6a8fa-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="6a8fa-108">Výklad těchto položek je stejný jako u metody [ICorProfilerInfo:: SetILInstrumentedCodeMap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6a8fa-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a8fa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a8fa-109">Remarks</span></span>  
 <span data-ttu-id="6a8fa-110">Nastavení mapování voláním této metody umožňuje ladicímu programu načíst mapování voláním [ICorDebugILCode2:: GetInstrumentedILMap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="6a8fa-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="6a8fa-111">Umožňuje také, aby ladicí program používal mapování interně při výpočtu posunu IL pro trasování zásobníku a pro dobu života proměnných.</span><span class="sxs-lookup"><span data-stu-id="6a8fa-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8fa-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a8fa-112">Requirements</span></span>  
 <span data-ttu-id="6a8fa-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8fa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8fa-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6a8fa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a8fa-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a8fa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a8fa-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8fa-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a8fa-117">See also</span></span>

- [<span data-ttu-id="6a8fa-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a8fa-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
