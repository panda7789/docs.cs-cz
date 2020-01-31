---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 476bcbd91188e3ff9eb63f50cfa2118a440b1a69
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868314"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 – rozhraní

Podtřída [ICorProfilerInfo7](icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda IsFunctionDynamic](icorprofilerinfo8-isfunctiondynamic-method.md)| Určuje, jestli funkce nemá přidružená metadata.|
|[Metoda GetFunctionFromIP3](icorprofilerinfo8-getfunctionfromip3-method.md)| Mapuje ukazatel na instrukci spravovaného kódu na FunctionID. Tato metoda spolupracuje s dynamickými i nedynamickými metodami. |
|[Metoda GetDynamicFunctionInfo](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Načte informace o dynamických metodách. |

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlavička:** CorProf. idl, CorProf. h  
**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
