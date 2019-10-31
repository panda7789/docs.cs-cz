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
ms.openlocfilehash: d9f0eff35dbe0058398d2d1c851ef85effa9cd28
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122413"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException – metoda
Označuje, zda má vlákno někdy neošetřenou výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 mimo Ukazatel na adresu seřazeného výčtu struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Vlákno mělo neošetřenou výjimku od jejího vytvoření.|  
|S_FALSE|Vlákno nikdy nemá neošetřenou výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda označuje, zda vlákno má někdy neošetřenou výjimku. V době spuštění neošetřeného zpětného volání výjimky nebo při zahájení nativního připojení JIT je zaručeno, že tato metoda vrátí hodnotu S_OK. Není zaručeno, že metoda [ICorDebugThread. GetCurrentException –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) vrátí neošetřenou výjimku; Nicméně pokud proces ještě nepokračoval po získání neošetřeného zpětného volání výjimky nebo po nativním připojení JIT. Kromě toho je možné (i když nepravděpodobné), aby měl více než jedno vlákno s neošetřenou výjimkou v době, kdy se spustí nativní JIT – připojit. V takovém případě neexistuje způsob, jak určit, která výjimka aktivovala připojení JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
