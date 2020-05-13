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
ms.openlocfilehash: 523d9665ffd2637a0e856d74d4d3b3838cb5e83c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212123"
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
 [in] `true` Chcete-li povolit vlastní oznámení ladicího programu; `false`zakážete oznámení. Výchozí hodnota je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `fEnable` je nastaveno na `true` , volání <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody spustí zpětné volání [ICorDebugManagedCallback3 –:: CustomNotification –](icordebugmanagedcallback3-customnotification-method.md) . Ve výchozím nastavení jsou oznámení zakázána. Proto musí ladicí program určit jakékoli typy oznámení, o kterých ví a který chce zpracovat. Vzhledem k tomu, že třída [ICorDebugClass](icordebug-interface.md) je vymezena aplikační doménou, ladicí program musí volat `SetEnableCustomNotification` pro každou doménu aplikace v procesu, pokud chce obdržet oznámení v celém procesu.  
  
 Od .NET Framework 4 je jediným podporovaným oznámením oznámení o závislostech mezi vlákny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess3 – rozhraní](icordebugprocess3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
