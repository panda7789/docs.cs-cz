---
title: ICorProfilerInfo7 – rozhraní
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495486"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 – rozhraní
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Podtřída [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , která poskytuje metodu pro použití nově definovaných metadat pro modul a který poskytuje přístup k datovému proudu symbolů v paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[ApplyMetaData – metoda](icorprofilerinfo7-applymetadata-method.md)|Aplikuje metadata nově definovaná `IMetadataEmit::Define*` metodami na zadaný modul.|  
|[GetInMemorySymbolsLength – metoda](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Vrátí délku datového proudu symbolů v paměti.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Načte bajty z datového proudu symbolů v paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
