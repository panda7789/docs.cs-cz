---
title: ICorProfilerInfo7 – rozhraní
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861746"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 – rozhraní
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Podtřída [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , která poskytuje metodu pro použití nově definovaných metadat pro modul a který poskytuje přístup k datovému proudu symbolů v paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ApplyMetaData – metoda](icorprofilerinfo7-applymetadata-method.md)|Aplikuje metadata nově definovaná metodami `IMetadataEmit::Define*` do zadaného modulu.|  
|[GetInMemorySymbolsLength – metoda](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Vrátí délku datového proudu symbolů v paměti.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Načte bajty z datového proudu symbolů v paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
