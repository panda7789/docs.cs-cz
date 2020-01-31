---
title: ICorDebugMergedAssemblyRecord – rozhraní
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: 6d5d862110cd91e8ac81c96e50486be10c579903
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793059"
---
# <a name="icordebugmergedassemblyrecord-interface"></a>ICorDebugMergedAssemblyRecord – rozhraní
Poskytuje informace o sloučeném sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCulture – metoda](icordebugmergedassemblyrecord-getculture-method.md)|Získá řetězec názvu jazykové verze sestavení.|  
|[GetIndex – metoda](icordebugmergedassemblyrecord-getindex-method.md)|Získá index předpony sestavení.|  
|[GetPublicKey – metoda](icordebugmergedassemblyrecord-getpublickey-method.md)|Získá veřejný klíč sestavení.|  
|[GetPublicKeyToken – metoda](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|Získá token veřejného klíče sestavení.|  
|[GetSimpleName – metoda](icordebugmergedassemblyrecord-getsimplename-method.md)|Získá jednoduchý název sestavení.|  
|[GetVersion – metoda](icordebugmergedassemblyrecord-getversion-method.md)|Získá informace o verzi sestavení.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
