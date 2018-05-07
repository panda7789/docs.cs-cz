---
title: ICorProfilerFunctionEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce5d5187ee4082bb851fa24bbcda2b099e37b89f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone – metoda
Získá ukazatele rozhraní v kopii [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel na ukazatel rozhraní, které se pak odkazuje na kopii této [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) rozhraní. Kopii enumerátor udržuje vlastní stav výčtu odděleně od této enumerátor. Pozice kurzoru počáteční vytvoření kopie je však stejný jako tento enumerátor aktuálním umístěním kurzoru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerFunctionEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
