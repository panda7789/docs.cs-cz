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
ms.openlocfilehash: 52ad124638a1c1ec7d39fa41b9163f3ab50ffe70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433066"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda
Získá nativní adresu a informace o snímku pro klauzuli Exception (`catch`/`finally`/`filter`), které mají být spuštěny nebo právě spuštěny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `pinfo`  
 mimo Ukazatel na strukturu [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) popisující aktuální instanci klauzule Exception a její přidružený rámec.  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení o výjimce lze `GetNotifiedExceptionClauseInfo` použít k získání nativní informace o adrese a snímku pro klauzuli Exception (`catch`/`finally`/`filter`), které mají být spuštěny ([ICorProfilerCallback:: ExceptionCatcherEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) zpětné volání je přijímáno profilerem) nebo právě spuštěn ([ICorProfilerCallback:: ExceptionCatcherLeave – ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyLeave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterLeave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) přijímá v profileru zpětné volání.  
  
 Toto volání lze provést kdykoli po jednom z výše uvedených zpětného volání, dokud se nepřijme odpovídající zpětné volání zákazu nebo je v aktuální klauzuli vyvolána vnořená výjimka, v takovém případě není pro tuto klauzuli k dispozici žádné oznámení. Všimněte si, že není možné vyvolané výjimce pro únik `filter` klauzule Exception, takže v takovém případě je vždy oznámení o zanechání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
