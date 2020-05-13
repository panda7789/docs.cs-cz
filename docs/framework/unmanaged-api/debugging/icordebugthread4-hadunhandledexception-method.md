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
ms.openlocfilehash: 4d954057c519263da49f8aaeeeef6ab9402b6956
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378378"
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
 mimo Ukazatel na adresu seřazeného výčtu struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Vlákno mělo neošetřenou výjimku od jejího vytvoření.|  
|S_FALSE|Vlákno nikdy nemá neošetřenou výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda označuje, zda vlákno má někdy neošetřenou výjimku. V době spuštění neošetřeného zpětného volání výjimky nebo zahájení inicializace nativní JIT-připojení je zaručena, že tato metoda vrátí S_OK. Není zaručeno, že metoda [ICorDebugThread. GetCurrentException –](icordebugthread-getcurrentexception-method.md) vrátí neošetřenou výjimku; Nicméně pokud proces ještě nepokračoval po získání neošetřeného zpětného volání výjimky nebo po nativním připojení JIT. Kromě toho je možné (i když nepravděpodobné), aby měl více než jedno vlákno s neošetřenou výjimkou v době, kdy se spustí nativní JIT – připojit. V takovém případě neexistuje způsob, jak určit, která výjimka aktivovala připojení JIT.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugThread4 – rozhraní](icordebugthread4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
