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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cb4bfdf90099719e2584c3767965a53186ca8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453255"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="00d69-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="00d69-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="00d69-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapování Common mezilehlá jazyk (CIL).</span><span class="sxs-lookup"><span data-stu-id="00d69-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d69-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00d69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d69-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="00d69-106">[v] Počet položek v mapě.</span><span class="sxs-lookup"><span data-stu-id="00d69-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="00d69-107">[v] Volající přidělené pole cor_il_map – položky.</span><span class="sxs-lookup"><span data-stu-id="00d69-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="00d69-108">Výklad tyto položky je stejný jako u [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="00d69-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d69-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00d69-109">Remarks</span></span>  
 <span data-ttu-id="00d69-110">Nastavení mapování voláním této metody umožní ladicí program k načtení mapování voláním [icordebugilcode2::getinstrumentedilmap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="00d69-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="00d69-111">Umožňuje také ladicí program interně použít mapování při výpočtu IL posune pro trasování zásobníku a proměnné životnosti.</span><span class="sxs-lookup"><span data-stu-id="00d69-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d69-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00d69-112">Requirements</span></span>  
 <span data-ttu-id="00d69-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d69-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d69-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00d69-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00d69-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00d69-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00d69-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d69-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d69-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d69-117">See Also</span></span>  
 [<span data-ttu-id="00d69-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00d69-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
