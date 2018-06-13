---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07606bf58709f088db486e0263e5cb519ab5b4cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456664"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="67ca6-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="67ca6-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="67ca6-103">Získá nativní adresy a rámce informace pro klauzuli výjimky (`catch`/`finally`/`filter`), má být spuštěna, nebo byla právě spuštěna.</span><span class="sxs-lookup"><span data-stu-id="67ca6-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ca6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67ca6-104">Syntax</span></span>  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67ca6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="67ca6-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="67ca6-106">[out] Ukazatel [cor_prf_ex_clause_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) struktura, která popisuje aktuální instance klauzule výjimky a jeho přidružené rámečku.</span><span class="sxs-lookup"><span data-stu-id="67ca6-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67ca6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67ca6-107">Remarks</span></span>  
 <span data-ttu-id="67ca6-108">Po přijetí oznámení o výjimce `GetNotifiedExceptionClauseInfo` lze použít k získání nativní adresy a rámce informací pro klauzuli výjimky (`catch`/`finally`/`filter`) se bude spuštěný ([ Icorprofilercallback::exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [icorprofilercallback::exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), nebo [icorprofilercallback::exceptionsearchfilterenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)zpětné volání je přijatých profileru) nebo má stačí spustit ([icorprofilercallback::exceptioncatcherleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [icorprofilercallback::exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), nebo [ Icorprofilercallback::exceptionsearchfilterleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) zpětné volání je přijatých profileru).</span><span class="sxs-lookup"><span data-stu-id="67ca6-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="67ca6-109">Toto volání lze provést kdykoli po jednu z výše uvedených zpětná volání Enter, dokud je přijatých odpovídající zpětného volání ponechejte nebo vnořené výjimce dojde v aktuální klauzuli, ve kterém je případě, že existuje žádná ponechejte oznámení pro tuto klauzuli.</span><span class="sxs-lookup"><span data-stu-id="67ca6-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="67ca6-110">Všimněte si, že není možné, abyste se vyhnuli vyvolaná výjimka `filter` klauzule výjimky, takže je vždy oznámení ponechejte v takovém případě.</span><span class="sxs-lookup"><span data-stu-id="67ca6-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ca6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67ca6-111">Requirements</span></span>  
 <span data-ttu-id="67ca6-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ca6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ca6-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67ca6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67ca6-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ca6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ca6-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ca6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ca6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="67ca6-116">See Also</span></span>  
 [<span data-ttu-id="67ca6-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67ca6-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="67ca6-118">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="67ca6-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
