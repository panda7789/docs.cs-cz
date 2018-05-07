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
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo – metoda
Získá nativní adresy a rámce informace pro klauzuli výjimky (`catch`/`finally`/`filter`), má být spuštěna, nebo byla právě spuštěna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pinfo`  
 [out] Ukazatel [cor_prf_ex_clause_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) struktura, která popisuje aktuální instance klauzule výjimky a jeho přidružené rámečku.  
  
## <a name="remarks"></a>Poznámky  
 Po přijetí oznámení o výjimce `GetNotifiedExceptionClauseInfo` lze použít k získání nativní adresy a rámce informací pro klauzuli výjimky (`catch`/`finally`/`filter`) se bude spuštěný ([ Icorprofilercallback::exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [icorprofilercallback::exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), nebo [icorprofilercallback::exceptionsearchfilterenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)zpětné volání je přijatých profileru) nebo má stačí spustit ([icorprofilercallback::exceptioncatcherleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [icorprofilercallback::exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), nebo [ Icorprofilercallback::exceptionsearchfilterleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) zpětné volání je přijatých profileru).  
  
 Toto volání lze provést kdykoli po jednu z výše uvedených zpětná volání Enter, dokud je přijatých odpovídající zpětného volání ponechejte nebo vnořené výjimce dojde v aktuální klauzuli, ve kterém je případě, že existuje žádná ponechejte oznámení pro tuto klauzuli. Všimněte si, že není možné, abyste se vyhnuli vyvolaná výjimka `filter` klauzule výjimky, takže je vždy oznámení ponechejte v takovém případě.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
