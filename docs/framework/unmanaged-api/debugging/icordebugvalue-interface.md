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
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396795"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue – rozhraní
Představuje hodnotu v laděném procesu. Hodnota může být čtení nebo hodnota zápisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](icordebugvalue-createbreakpoint-method.md)|Tato metoda není v současnosti implementována.|  
|[GetAddress – metoda](icordebugvalue-getaddress-method.md)|Získá adresu tohoto `ICorDebugValue` objektu, který je právě laděn.|  
|[GetSize – metoda](icordebugvalue-getsize-method.md)|Získá velikost tohoto objektu v bajtech `ICorDebugValue` .|  
|[GetType – metoda](icordebugvalue-gettype-method.md)|Získá primitivní typ tohoto `ICorDebugValue` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, že vlastnictví objektu hodnoty je předáno při jeho vrácení. Příjemce je zodpovědný za odebrání odkazu z objektu po jeho dokončení s objektem.  
  
 V závislosti na tom, odkud byla hodnota načtena, nemusí tato hodnota po obnovení procesu zůstat platná. Obecně platí, že hodnota by neměla být držena v rámci volání metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugValue3 – rozhraní](icordebugvalue3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
