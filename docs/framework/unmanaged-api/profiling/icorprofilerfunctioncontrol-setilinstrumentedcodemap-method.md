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
ms.openlocfilehash: b36439dd6fb882bb41c38e953cb7b1c5f2b93d30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074102"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="660fc-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="660fc-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="660fc-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="660fc-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="660fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="660fc-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="660fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="660fc-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="660fc-106">[in] Počet položek v objektu map.</span><span class="sxs-lookup"><span data-stu-id="660fc-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="660fc-107">[in] Pole přidělené volajícímu cor_il_map – položek.</span><span class="sxs-lookup"><span data-stu-id="660fc-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="660fc-108">Interpretace těchto položek, které je stejné jako v případě [icorprofilerinfo::setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="660fc-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="660fc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="660fc-109">Remarks</span></span>  
 <span data-ttu-id="660fc-110">Nastavení mapování zavoláním této metody umožní ladicího programu k načtení mapování voláním [icordebugilcode2::getinstrumentedilmap –](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="660fc-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="660fc-111">Také to umožňuje ladicímu programu používat mapování interně při výpočtu IL dorovnání u trasování zásobníku a životnost proměnné.</span><span class="sxs-lookup"><span data-stu-id="660fc-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="660fc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="660fc-112">Requirements</span></span>  
 <span data-ttu-id="660fc-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="660fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="660fc-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="660fc-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="660fc-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="660fc-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="660fc-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="660fc-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="660fc-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="660fc-117">See also</span></span>

- [<span data-ttu-id="660fc-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="660fc-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
