---
title: ICorDebugProcess3::SetEnableCustomNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129709"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification – metoda
Povolí nebo zakáže oznámení vlastního ladicího programu určeného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 pro Typ, který určuje vlastní oznámení ladicího programu.  
  
 `fEnable`  
 [in] `true` povolit oznámení vlastního ladicího programu; `false` zakázat oznámení. Výchozí hodnota je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je `fEnable` nastaveno na `true`, volání metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> spustí zpětné volání [ICorDebugManagedCallback3 –:: CustomNotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) . Ve výchozím nastavení jsou oznámení zakázána. Proto musí ladicí program určit jakékoli typy oznámení, o kterých ví a který chce zpracovat. Vzhledem k tomu, že třída [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) je vymezena doménou aplikace, ladicí program musí volat `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chce obdržet oznámení v celém procesu.  
  
 Od .NET Framework 4 je jediným podporovaným oznámením oznámení o závislostech mezi vlákny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
