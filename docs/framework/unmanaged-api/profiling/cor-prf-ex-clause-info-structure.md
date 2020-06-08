---
title: COR_PRF_EX_CLAUSE_INFO – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: 5c764031f709eefe61022d0662f37bc5d3f3e281
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500998"
---
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO – struktura
Ukládá informace o konkrétní instanci klauzule Exception a jejím přidruženém rámci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`clauseType`|Hodnota výčtu [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) , která určuje typ klauzule Exception, který kód právě zadal nebo Left.|  
|`programCounter`|Nativní vstupní bod obslužné rutiny klauzule – například obsah EIP registru x86.|  
|`framePointer`|Ukazatel na logický rámec pro obslužnou rutinu klauzule, například obsah EBP registru x86.|  
|`shadowStackPointer`|Ukazatel na stínový zásobník. Tato hodnota je obsahem registru BSP a vztahuje se pouze na IA64.|  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení výjimky lze pomocí [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo –](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) získat nativní informace o adrese a snímku pro klauzuli Exception ( `catch` / `finally` /Filter), která má být spuštěna nebo právě spuštěna.  
  
 Provádění klauzule Exception zahrnuje tato zpětná volání z modulu CLR (Common Language Runtime):  
  
- [ICorProfilerCallback:: ExceptionCatcherEnter –](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyEnter –](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterEnter –](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionCatcherLeave –](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyLeave –](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterLeave –](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](profiling-structures.md)
