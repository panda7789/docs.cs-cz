---
title: ICorDebugManagedCallback3::CustomNotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 8a4620e591cc80efb5c0fd53b0edf3a35849c421
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209757"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification – metoda
Indikuje, že se aktivovalo oznámení vlastního ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThread`  
 pro Ukazatel na vlákno, které vyvolalo oznámení.  
  
 `pAppDomain`  
 pro Ukazatel na doménu aplikace obsahující vlákno, které vyvolalo oznámení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Následné volání metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification –](icordebugthread4-getcurrentcustomdebuggernotification-method.md) načte objekt vlákna, který byl předán <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metodě. Typ objektu vlákna musí být dříve povolen voláním metody [ICorDebugProcess3 –:: SetEnableCustomNotification –](icordebugprocess3-setenablecustomnotification-method.md) . Ladicí program může číst parametry specifické pro typ z polí objektu vlákna a může ukládat odpovědi do polí.  
  
 Rozhraní [ICorDebug](icordebug-interface.md) neukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontraktem mezi ladicími programy, aplikacemi a .NET Framework.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback3 – rozhraní](icordebugmanagedcallback3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
