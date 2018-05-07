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
ms.openlocfilehash: f5a4a6bc7b1e79068b11b099352cec64dd09f301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread – metoda
Inicializuje aktuální vlákno předem následné profileru, které volání rozhraní API ve stejném vlákně, takže se vyhnout této vzájemného zablokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Doporučujeme vám, že zavoláte `InitializeCurrentThread` na jakékoli vlákno, které bude volat profileru rozhraní API, protože existují pozastaveno vláken. Tato metoda se obvykle používá ve profilery vzorkování, které vytvořit své vlastní vlákno k volání [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu za účelem zásobníku provede při cíl vlákno je pozastaveno. Při volání `InitializeCurrentThread` po profileru při první vytvoří vlákno vzorkování, profilery můžete zajistit, že inicializaci opožděné podle vláken, která modulu CLR by jinak prováděných při prvním volání `DoStackSnapshot` nyní dochází bezpečně když jsou nejsou žádná jiná vlákna pozastaveno.  
  
> [!NOTE]
>  `InitializeCurrentThread` provede inicializaci předem na dokončení úlohy, které trvat zámků a může zablokování. Volání `InitializeCurrentThread` jenom v případě, že neexistují žádné pozastavenou vláken.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
