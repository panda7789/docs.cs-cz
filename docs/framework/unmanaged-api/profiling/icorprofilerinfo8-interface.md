---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495161"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 – rozhraní

Podtřída [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.

## <a name="methods"></a>Metody  

| Metoda|Description|  
| ------------|-----------------|  
|[IsFunctionDynamic – metoda](icorprofilerinfo8-isfunctiondynamic-method.md)| Určuje, jestli funkce nemá přidružená metadata.|
|[GetFunctionFromIP3 – metoda](icorprofilerinfo8-getfunctionfromip3-method.md)| Mapuje ukazatel na instrukci spravovaného kódu na FunctionID. Tato metoda spolupracuje s dynamickými i nedynamickými metodami. |
|[GetDynamicFunctionInfo – metoda](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Načte informace o dynamických metodách. |

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
**Hlavička:** CorProf. idl, CorProf. h  
**Verze .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
