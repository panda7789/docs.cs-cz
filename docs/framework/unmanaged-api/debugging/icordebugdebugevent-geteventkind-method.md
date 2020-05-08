---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976392"
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
 Ukazatel na člen výčtu [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , který určuje typ události.  
  
## <a name="remarks"></a>Poznámky  
 Na základě hodnoty `pDebugEventKind`můžete zavolat `QueryInterface` pro získání přesnější rozhraní události ladění, které má další data.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugDebugEvent](icordebugdebugevent-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
