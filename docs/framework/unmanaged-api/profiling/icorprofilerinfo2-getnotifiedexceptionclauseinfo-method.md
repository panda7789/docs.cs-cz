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
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda
Získá nativní adresu a informace o snímku pro klauzuli Exception ( `catch` / `finally` / `filter` ), která má být spuštěna nebo právě byla spuštěna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `pinfo`  
 mimo Ukazatel na strukturu [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) popisující aktuální instanci klauzule Exception a její přidružený rámec.  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení o výjimce `GetNotifiedExceptionClauseInfo` lze použít k získání nativní informace o adrese a snímku pro klauzuli výjimky ( `catch` / `finally` / `filter` ), která má být spuštěna ([ICorProfilerCallback:: ExceptionCatcherEnter –](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyEnter –](icorprofilercallback-exceptionunwindfinallyenter-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterEnter –](icorprofilercallback-exceptionsearchfilterenter-method.md) zpětné volání je přijímáno profilerem) nebo právě bylo spuštěno ([ICorProfilerCallback:: ExceptionCatcherLeave –](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyLeave –](icorprofilercallback-exceptionunwindfinallyleave-method.md)nebo [ICorProfilerCallback:: ExceptionSearchFilterLeave –](icorprofilercallback-exceptionsearchfilterleave-method.md) zpětné volání, které je obdrženo profilerem).  
  
 Toto volání lze provést kdykoli po jednom z výše uvedených zpětného volání, dokud se nepřijme odpovídající zpětné volání zákazu nebo je v aktuální klauzuli vyvolána vnořená výjimka, v takovém případě není pro tuto klauzuli k dispozici žádné oznámení. Všimněte si, že není možné vyvolanou výjimku použít k úniku `filter` klauzule Exception, takže v takovém případě je vždy oznámení o zanechání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
