---
title: ICorProfilerInfo4::InitializeCurrentThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fd0900e61c57d105439d83430284dc8634d2a1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000503"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread – metoda
Inicializuje aktuální vlákno s předstihem následné profiler volání rozhraní API ve stejném vlákně, takže se lze vyvarovat této zablokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Doporučujeme vám, že zavoláte `InitializeCurrentThread` v libovolném vlákně, který bude volat profilování rozhraní API, i když existují pozastavená vlákna. Tato metoda je obvykle používána vzorkování profilovací programy, které vytvoření vlastních vláken k volání [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu za účelem zásobníku vás během cílové vlákno je pozastaveno. Voláním `InitializeCurrentThread` až když profiler nejprve vytvoří vlákno vzorkování, profilery můžete zajistit, že opožděná vlákno inicializace, které modul CLR by jinak provádět při prvním volání `DoStackSnapshot` nyní provést bezpečně kdy mají být nejsou žádná jiná vlákna pozastaveno.  
  
> [!NOTE]
>  `InitializeCurrentThread` provede inicializaci předem na dokončení úlohy, které povede a může zablokování. Volání `InitializeCurrentThread` pouze v případě, že neexistují žádná pozastavená vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
