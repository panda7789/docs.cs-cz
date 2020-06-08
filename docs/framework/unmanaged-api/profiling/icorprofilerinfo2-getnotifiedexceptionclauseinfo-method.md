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
ms.openlocfilehash: 08337a118a80d213f16e2a16f744b96f5dde2e7f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496994"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="ffb22-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="ffb22-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="ffb22-103">Získá nativní adresu a informace o snímku pro klauzuli Exception ( `catch` / `finally` / `filter` ), která má být spuštěna nebo právě byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="ffb22-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffb22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffb22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffb22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffb22-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="ffb22-106">mimo Ukazatel na strukturu [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) popisující aktuální instanci klauzule Exception a její přidružený rámec.</span><span class="sxs-lookup"><span data-stu-id="ffb22-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffb22-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffb22-107">Remarks</span></span>  
 <span data-ttu-id="ffb22-108">Po přijetí oznámení o výjimce `GetNotifiedExceptionClauseInfo` lze použít k získání nativní informace o adrese a snímku pro klauzuli výjimky ( `catch` / `finally` / `filter` ), která má být spuštěna ([ICorProfilerCallback:: ExceptionCatcherEnter –](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyEnter –](icorprofilercallback-exceptionunwindfinallyenter-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterEnter –](icorprofilercallback-exceptionsearchfilterenter-method.md) zpětné volání je přijímáno profilerem) nebo právě bylo spuštěno ([ICorProfilerCallback:: ExceptionCatcherLeave –](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyLeave –](icorprofilercallback-exceptionunwindfinallyleave-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterLeave –](icorprofilercallback-exceptionsearchfilterleave-method.md) zpětné volání, které je obdrženo profilerem).</span><span class="sxs-lookup"><span data-stu-id="ffb22-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="ffb22-109">Toto volání lze provést kdykoli po jednom z výše uvedených zpětného volání, dokud se nepřijme odpovídající zpětné volání zákazu nebo je v aktuální klauzuli vyvolána vnořená výjimka, v takovém případě není pro tuto klauzuli k dispozici žádné oznámení.</span><span class="sxs-lookup"><span data-stu-id="ffb22-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="ffb22-110">Všimněte si, že není možné vyvolanou výjimku použít k úniku `filter` klauzule Exception, takže v takovém případě je vždy oznámení o zanechání.</span><span class="sxs-lookup"><span data-stu-id="ffb22-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffb22-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ffb22-111">Requirements</span></span>  
 <span data-ttu-id="ffb22-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffb22-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffb22-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ffb22-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffb22-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ffb22-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffb22-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffb22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffb22-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ffb22-116">See also</span></span>

- [<span data-ttu-id="ffb22-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffb22-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ffb22-118">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ffb22-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
