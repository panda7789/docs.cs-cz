---
title: ICorProfilerCallback3::ProfilerDetachSucceeded – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: b96a8930c24275546b0aac9fa650cf5447ef4ef2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865412"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded – metoda
Upozorní profileru, že modul CLR (Common Language Runtime) chystá uvolnění knihovny DLL profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota z tohoto zpětného volání je ignorována.  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání `ProfilerDetachSucceeded` je vystaveno po ukončení všech vláken v kódu profileru. Při volání této metody by Profiler měl provést všechny poslední minutové úkoly, které nejsou vhodné pro svůj destruktor, jako je například oznamování jeho uživatelského rozhraní nebo komponenty protokolování. Profiler však nesmí volat funkce v rozhraních, která jsou poskytována modulem CLR během tohoto zpětného volání (například rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) nebo `IMetaData*`).  
  
 Modul CLR vytvoří položku v protokolu událostí aplikace systému Windows, která indikuje, že operace odpojení je úspěšná.  
  
 Poté, co Profiler vrátí z tohoto zpětného volání, modul CLR uvolní objekt profileru a uvolní knihovnu DLL profileru. Proto profiler nesmí provádět žádné akce, které by mohly způsobit, že by došlo k provedení v rámci knihovny DLL profileru po návratu z tohoto zpětného volání. Například nesmí vytvářet vlákna nebo registrovat zpětná volání časovače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
