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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efe3070b41b1d71e0cf533a7f9f211f4c6626726
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197854"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded – metoda
Oznámí profileru, že modul CLR (CLR) se chystá uvolnění knihovny DLL profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota vrácená z této zpětné volání se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 `ProfilerDetachSucceeded` Zpětného volání je vydána po všechna vlákna odpojili profileru kód. Když tato metoda je volána, profiler by měl provádět žádné poslední minuty úlohy, které nejsou vhodné pro jeho destruktor, jako je například upozornění jeho uživatelské rozhraní nebo protokolování součásti. Však nesmí volat funkce rozhraní, které jsou k dispozici v modulu CLR při tomto zpětném volání profileru (například [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo `IMetaData*` rozhraní).  
  
 Modul CLR vytvoří záznam v protokolu událostí Windows aplikace označující, jestli se operace odpojení úspěšně dokončila.  
  
 Po profiler vrátí z této zpětné volání, CLR uvolní objekt profileru a uvolní profiler DLL. Proto profiler nesmí provádět všechny akce, které by mohly způsobit provedení dotazu uvnitř knihovny DLL profileru po jeho vrácení z této zpětné volání. Například se nesmí vytvořit vlákna nebo registrace zpětných volání časovače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
