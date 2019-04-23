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
ms.openlocfilehash: cabe2f1ad5b586fed24c7317bb3a7b8407e09158
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167008"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda
Získá nativní rámce informace o adrese a pro klauzuli výjimky (`catch`/`finally`/`filter`), který má být spuštěna, nebo jenom nebyly spuštěny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `pinfo`  
 [out] Ukazatel [cor_prf_ex_clause_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) struktura, která popisuje aktuální klauzuli instance výjimky a jeho přidružené rámce.  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení o výjimce `GetNotifiedExceptionClauseInfo` můžete použít k získání nativní rámce informace o adrese a pro klauzuli výjimky (`catch`/`finally`/`filter`), který se spustí ([ Icorprofilercallback::exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [icorprofilercallback::exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), nebo [icorprofilercallback::exceptionsearchfilterenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)přijme zpětného volání profileru) nebo pouze nebyly spuštěny ([icorprofilercallback::exceptioncatcherleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [icorprofilercallback::exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), nebo [ Icorprofilercallback::exceptionsearchfilterleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) přijme zpětného volání profileru).  
  
 Toto volání lze provést kdykoli po jednu z výše uvedených zpětná volání Enter, dokud nebude odpovídající zpětnému volání nechte přijetí nebo vnořená výjimka je vyvolána v aktuální klauzuli, ve kterém je případě, že existuje žádné nechte oznámení pro tuto klauzuli. Mějte na paměti, že není možné pro vyvolanou výjimku k návratu `filter` výjimka klauzule, takže je vždy nechte oznámení v takovém případě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
