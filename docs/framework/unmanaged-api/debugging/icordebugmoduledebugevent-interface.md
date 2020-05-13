---
title: ICorDebugModuleDebugEvent – rozhraní
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213330"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent – rozhraní
Rozšiřuje rozhraní [ICorDebugDebugEvent](icordebugdebugevent-interface.md) pro podporu událostí na úrovni modulu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule – metoda](icordebugmoduledebugevent-getmodule-method.md)|Získá sloučený modul, který byl právě načten nebo uvolněn.|  
  
## <a name="remarks"></a>Poznámky  
 Typy událostí [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) a [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implementují toto rozhraní.  
  
> [!NOTE]
> Rozhraní je k dispozici pouze s .NET Native. Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
