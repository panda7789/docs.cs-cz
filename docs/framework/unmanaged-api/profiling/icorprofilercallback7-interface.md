---
title: ICorProfilerCallback7 Interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c49a5f782ea105ce57b5fbc2c6bd9bd89f708d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629578"
---
# <a name="icorprofilercallback7-interface"></a>ICorProfilerCallback7 Interface
[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]  
  
 Podtřída [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) , která poskytuje metodu zpětného volání, která používá modul common language runtime pro oznámení profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|Oznámí profileru, je aktualizovaný symbol proud přidružený k modulu v paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
