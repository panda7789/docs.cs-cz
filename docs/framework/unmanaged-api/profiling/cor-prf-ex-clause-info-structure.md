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
ms.openlocfilehash: df4bfe69b22439073342693a03376a0b506f9c70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428370"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`clauseType`|Hodnota výčtu [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) , která určuje typ klauzule Exception, který kód právě zadal nebo Left.|  
|`programCounter`|Nativní vstupní bod obslužné rutiny klauzule – například obsah EIP registru x86.|  
|`framePointer`|Ukazatel na logický rámec pro obslužnou rutinu klauzule, například obsah EBP registru x86.|  
|`shadowStackPointer`|Ukazatel na stínový zásobník. Tato hodnota je obsahem registru BSP a vztahuje se pouze na IA64.|  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení výjimky lze pomocí [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) získat nativní informace o adrese a snímku pro klauzuli exception (`catch`/`finally`/Filter), která má být spuštěna nebo právě spuštěna.  
  
 Provádění klauzule Exception zahrnuje tato zpětná volání z modulu CLR (Common Language Runtime):  
  
- [ICorProfilerCallback:: ExceptionCatcherEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterEnter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback:: ExceptionCatcherLeave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyLeave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionSearchFilterLeave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
