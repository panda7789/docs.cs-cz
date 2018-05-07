---
title: ICorProfilerCallback::ClassLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 671f6743915ae4b7e7f4147f9fcddb1a623916ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished – metoda
Upozorní profileru, že třídu dokončil načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [v] Určuje třídu, která byla načtena.  
  
 `hrStatus`  
 [v] HRESULT, která určuje, zda třída úspěšně načten.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `classId` není platná pro požadavek informace, dokud `ClassLoadFinished` metoda je volána.  
  
 Některé části načítání třída může pokračovat po `ClassLoadFinished` zpětného volání. Selhání HRESULT v `hrStatus` znamená chybu. Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část načítání třída proběhl úspěšně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
