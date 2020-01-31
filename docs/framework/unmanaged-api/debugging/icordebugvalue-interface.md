---
title: ICorDebugValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791141"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue – rozhraní
Představuje hodnotu v laděném procesu. Hodnota může být čtení nebo hodnota zápisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](icordebugvalue-createbreakpoint-method.md)|Tato metoda není v současnosti implementována.|  
|[GetAddress – metoda](icordebugvalue-getaddress-method.md)|Získá adresu tohoto objektu `ICorDebugValue`, který je právě laděn.|  
|[GetSize – metoda](icordebugvalue-getsize-method.md)|Získá velikost objektu `ICorDebugValue` v bajtech.|  
|[GetType – metoda](icordebugvalue-gettype-method.md)|Získá primitivní typ tohoto objektu `ICorDebugValue`.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, že vlastnictví objektu hodnoty je předáno při jeho vrácení. Příjemce je zodpovědný za odebrání odkazu z objektu po jeho dokončení s objektem.  
  
 V závislosti na tom, odkud byla hodnota načtena, nemusí tato hodnota po obnovení procesu zůstat platná. Obecně platí, že hodnota by neměla být držena v rámci volání metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugValue3 – rozhraní](icordebugvalue3-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
