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
ms.openlocfilehash: 93406dddf7babd8cf61032666737b993c2f721f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499594"
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
 `ProfilerDetachSucceeded`Zpětné volání je vystaveno po ukončení všech vláken v kódu profileru. Při volání této metody by Profiler měl provést všechny poslední minutové úkoly, které nejsou vhodné pro svůj destruktor, jako je například oznamování jeho uživatelského rozhraní nebo komponenty protokolování. Profiler však nesmí volat funkce v rozhraních, která jsou poskytována modulem CLR během tohoto zpětného volání (například [ICorProfilerInfo](icorprofilerinfo-interface.md) nebo `IMetaData*` rozhraní).  
  
 Modul CLR vytvoří položku v protokolu událostí aplikace systému Windows, která indikuje, že operace odpojení je úspěšná.  
  
 Poté, co Profiler vrátí z tohoto zpětného volání, modul CLR uvolní objekt profileru a uvolní knihovnu DLL profileru. Proto profiler nesmí provádět žádné akce, které by mohly způsobit, že by došlo k provedení v rámci knihovny DLL profileru po návratu z tohoto zpětného volání. Například nesmí vytvářet vlákna nebo registrovat zpětná volání časovače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
