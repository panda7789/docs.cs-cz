---
title: Rozhraní ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 1c598d23cac77e50cf302e6936b88b5eb6e558c2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976431"
---
# <a name="icordebugdatatarget2-interface"></a>Rozhraní ICorDebugDataTarget2
Logicky rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateVirtualUnwinder – metoda](icordebugdatatarget2-createvirtualunwinder-method.md)|Vytvoří novou odvinoutho zásobníku, který spustí odvinutí z počátečního kontextu (což není nutně listem vlákna).|  
|[EnumerateThreadIDs – metoda](icordebugdatatarget2-enumeratethreadids-method.md)|Vrátí seznam identifikátorů aktivních vláken.|  
|[GetImageFromPointer – metoda](icordebugdatatarget2-getimagefrompointer-method.md)|Vrátí základní adresu modulu a velikost z adresy v tomto modulu.|  
|[GetImageLocation – metoda](icordebugdatatarget2-getimagelocation-method.md)|Vrátí cestu modulu ze základní adresy modulu.|  
|[GetSymbolProviderForImage – metoda](icordebugdatatarget2-getsymbolproviderforimage-method.md)|Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní je dostupné jenom pro .NET Native. Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
