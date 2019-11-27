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
ms.openlocfilehash: 39882a554f9d47040bef00ff320d15b56abea533
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445725"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread – metoda
Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Doporučujeme, abyste volali `InitializeCurrentThread` na jakémkoli vlákně, které bude volat rozhraní API profileru, když dojde k pozastaveným vláknům. Tato metoda je obvykle používána vzorkovacími profily, které vytvoří vlastní vlákno pro volání metody [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) pro provádění procházení zásobníku, zatímco cílové vlákno je pozastaveno. Zavoláním `InitializeCurrentThread`, když Profiler nejprve vytvoří vlákno vzorkování, profilery mohou zajistit, že při prvním volání metody, které by CLR jinak prováděl během prvního volání `DoStackSnapshot`, může nyní dojít k bezpečnému výskytu v případě, že nejsou pozastavena žádná jiná vlákna.  
  
> [!NOTE]
> `InitializeCurrentThread` provede inicializaci předem k dokončení úkolů, které přijímají zámky, a může zablokovat. Volání `InitializeCurrentThread` pouze v případě, že nejsou k dispozici žádná pozastavená vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
