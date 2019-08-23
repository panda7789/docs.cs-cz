---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911343"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind – metoda
Určuje, jaký druh události tento `ICorDebugDebugEvent` objekt představuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pDebugEventKind  
 Ukazatel na člen výčtu [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) , který určuje typ události.  
  
## <a name="remarks"></a>Poznámky  
 Na základě hodnoty `pDebugEventKind`můžete zavolat `QueryInterface` pro získání přesnější rozhraní události ladění, které má další data.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
