---
title: ICorProfilerInfo6 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: fba57a88cd3af582b4edf0e5bdbf6ac48020c9f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495501"
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6 – rozhraní
[Podporováno v .NET Framework 4,6 a novějších verzích]  
  
 Podtřída [ICorProfilerInfo5](icorprofilerinfo5-interface.md) , která poskytuje enumerátor pro všechny metody, které jsou definovány v daném modulu Ngen a vloženy danou metodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|Vrátí enumerátor pro všechny metody, které patří do daného modulu NGen a které jsou vloženy v těle dané metody.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
