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
ms.openlocfilehash: 31caa87b1eaa48532ffb20b46c593242379c7ae8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780348"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="dbd2a-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="dbd2a-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="dbd2a-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="dbd2a-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbd2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbd2a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbd2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbd2a-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="dbd2a-106">[in] Počet položek v objektu map.</span><span class="sxs-lookup"><span data-stu-id="dbd2a-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="dbd2a-107">[in] Pole přidělené volajícímu cor_il_map – položek.</span><span class="sxs-lookup"><span data-stu-id="dbd2a-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="dbd2a-108">Interpretace těchto položek, které je stejné jako v případě [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="dbd2a-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbd2a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbd2a-109">Remarks</span></span>  
 <span data-ttu-id="dbd2a-110">Nastavení mapování zavoláním této metody umožní ladicího programu k načtení mapování voláním [icordebugilcode2::getinstrumentedilmap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="dbd2a-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="dbd2a-111">Také to umožňuje ladicímu programu používat mapování interně při výpočtu IL dorovnání u trasování zásobníku a životnost proměnné.</span><span class="sxs-lookup"><span data-stu-id="dbd2a-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbd2a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbd2a-112">Requirements</span></span>  
 <span data-ttu-id="dbd2a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd2a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbd2a-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dbd2a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbd2a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbd2a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbd2a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd2a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbd2a-117">See also</span></span>

- [<span data-ttu-id="dbd2a-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbd2a-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
