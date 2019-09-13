---
title: ICorProfilerInfo8 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928940"
---
# <a name="icorprofilerinfo8-interface"></a>ICorProfilerInfo8 – rozhraní

Podtřída [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) , která poskytuje metody pro dotazování na informace o dynamických metodách.

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda IsFunctionDynamic](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| Určuje, jestli funkce nemá přidružená metadata.|
|[Metoda GetFunctionFromIP3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| Mapuje ukazatel na instrukci spravovaného kódu na FunctionID. Tato metoda spolupracuje s dynamickými i nedynamickými metodami. |
|[Metoda GetDynamicFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| Načte informace o dynamických metodách. |

## <a name="requirements"></a>Požadavky  
**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
**Hlaviček** CorProf.idl, CorProf.h  
**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
