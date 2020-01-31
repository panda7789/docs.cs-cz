---
title: Rozhraní ICorDebugLoadedModule
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 9d3bdcec9e90dab337b595294d114de4bd3d531f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781989"
---
# <a name="icordebugloadedmodule-interface"></a>Rozhraní ICorDebugLoadedModule
Poskytuje informace o načteném modulu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetBaseAddress – metoda](icordebugloadedmodule-getbaseaddress-method.md)|Načte základní adresu načteného modulu.|  
|[GetName – metoda](icordebugloadedmodule-getname-method.md)|Získá název načteného modulu.|  
|[GetSize – metoda](icordebugloadedmodule-getsize-method.md)|Získá velikost načteného modulu v bajtech.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugLoadedModule` je implementováno pomocí ladicího programu a používá rozhraní ladění CLR k získání informací o načteném modulu z ladicího programu.  
  
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
