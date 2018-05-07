---
title: ICorDebugThread4::HadUnhandledException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException – metoda
Určuje, zda vlákno někdy došlo k neošetřené výjimce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Ukazatel na adresu seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Vlákno došlo k neošetřené výjimce od svého vytvoření.|  
|S_FALSE|Vlákno nikdy došlo k neošetřené výjimce.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda určuje, zda vlákno někdy došlo k neošetřené výjimce. V čase se aktivuje zpětného volání neošetřené výjimky nebo nativní JIT – připojené se zahájí, tato metoda záruku, že se vrátíte S_OK. Neexistuje žádná záruka, [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) metoda vrátí neošetřené výjimce; však bude, pokud proces nebyl ještě pokračuje po získání zpětné volání neošetřené výjimky nebo po nativní JIT – připojené. Kromě toho je možné (Ačkoli je to pravděpodobně) má více než jedno vlákno s k neošetřené výjimce v době nativní JIT – připojené se aktivuje. V takovém případě není žádný způsob, jak určit, která výjimka aktivaci JIT – připojené.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
