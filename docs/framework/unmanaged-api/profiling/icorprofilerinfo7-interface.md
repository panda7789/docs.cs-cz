---
title: ICorProfilerInfo7 Interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c33e620b861f1065f95ba9f1f732911723c16f88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526272"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 Interface
[Podporované v [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]  
  
 Podtřída [icorprofilerinfo6 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) , který poskytuje způsob, jak použít nově definované v modulu metadat, který poskytuje přístup k datovému proudu symbolu v paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyMetaData – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.|  
|[GetInMemorySymbolsLength – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|Vrátí délku datového proudu symbolu v paměti.|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|Přečte bajtů ze symbolů v paměti datového proudu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
