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
ms.openlocfilehash: 83192fd2d24e740ab470988531db823b34df4494
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131427"
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
 Následné volání metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) načte objekt vlákna, který byl předán metodě <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>. Typ objektu vlákna musí být dříve povolen voláním metody [ICorDebugProcess3 –:: SetEnableCustomNotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) . Ladicí program může číst parametry specifické pro typ z polí objektu vlákna a může ukládat odpovědi do polí.  
  
 Rozhraní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) neukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontraktem mezi ladicími programy, aplikacemi a .NET Framework.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
