---
title: ICorDebugDebugEvent::GetEventKind – metoda
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783416"
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind – metoda
Určuje, jaký typ události tento objekt `ICorDebugDebugEvent` představuje.  
  
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
 Na základě hodnoty `pDebugEventKind`můžete volat `QueryInterface` a získat tak přesnější rozhraní události ladění, které obsahuje další data.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDebugEvent – rozhraní](icordebugdebugevent-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
