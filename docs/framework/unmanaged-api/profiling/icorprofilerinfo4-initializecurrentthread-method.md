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
ms.openlocfilehash: 1f3ff3e9b68aa30f424f4b2fe6c7cacd2cddd544
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495928"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread – metoda
Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Doporučujeme, abyste volali `InitializeCurrentThread` jakékoli vlákno, které bude volat rozhraní API profileru, když dojde k pozastaveným vláknům. Tato metoda je obvykle používána vzorkovacími profily, které vytvoří vlastní vlákno pro volání metody [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) pro provádění procházení zásobníku, zatímco cílové vlákno je pozastaveno. Zavoláním metody `InitializeCurrentThread` jednou, když Profiler nejprve vytvoří vlákno vzorkování, profilery mohou zajistit, aby při opožděné inicializaci po vláknech, které by CLR jinak prováděly během prvního volání, bylo `DoStackSnapshot` nyní možné bezpečně vyskytnout, když nejsou žádná jiná vlákna pozastavena.  
  
> [!NOTE]
> `InitializeCurrentThread`provádí inicializaci předem úlohy, které přijímají zámky a mohou zablokovat. Volat `InitializeCurrentThread` pouze v případě, že nejsou k dispozici žádná pozastavená vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
