---
title: "ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 580d60fe0a6348a163fef9e215cddfc1bc4302b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="d056f-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="d056f-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="d056f-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapování Common mezilehlá jazyk (CIL).</span><span class="sxs-lookup"><span data-stu-id="d056f-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d056f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d056f-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d056f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d056f-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="d056f-106">[v] Počet položek v mapě.</span><span class="sxs-lookup"><span data-stu-id="d056f-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="d056f-107">[v] Volající přidělené pole cor_il_map – položky.</span><span class="sxs-lookup"><span data-stu-id="d056f-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="d056f-108">Výklad tyto položky je stejný jako u [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="d056f-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d056f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d056f-109">Remarks</span></span>  
 <span data-ttu-id="d056f-110">Nastavení mapování voláním této metody umožní ladicí program k načtení mapování voláním [icordebugilcode2::getinstrumentedilmap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="d056f-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="d056f-111">Umožňuje také ladicí program interně použít mapování při výpočtu IL posune pro trasování zásobníku a proměnné životnosti.</span><span class="sxs-lookup"><span data-stu-id="d056f-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d056f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d056f-112">Requirements</span></span>  
 <span data-ttu-id="d056f-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d056f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d056f-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d056f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d056f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d056f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d056f-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d056f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d056f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d056f-117">See Also</span></span>  
 [<span data-ttu-id="d056f-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d056f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
