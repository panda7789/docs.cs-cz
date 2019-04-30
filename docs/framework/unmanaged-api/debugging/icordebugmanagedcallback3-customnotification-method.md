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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914859"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification – metoda
Označuje, že vlastní oznámení ladicího programu bylo vyvoláno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThread`  
 [in] Ukazatel na vlákno, které vyvolá oznámení.  
  
 `pAppDomain`  
 [in] Ukazatel na doménu aplikace, která obsahuje podproces, který vyvolá oznámení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Následné volání [icordebugthread4::getcurrentcustomdebuggernotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda načte objekt vlákna, která byla předána <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody. Typ objektu vlákna musí být dříve povolen voláním [icordebugprocess3::setenablecustomnotification –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metody. Ladicí program může číst parametry pro konkrétní typ z polí objekt vlákna a můžete ukládání odpovědí do polí.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozhraní ukládá žádné zásady na typy oznámení nebo jejich obsah a sémantika oznámení je výhradně kontrakt mezi ladicích programů, aplikací a rozhraní .NET Framework.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
