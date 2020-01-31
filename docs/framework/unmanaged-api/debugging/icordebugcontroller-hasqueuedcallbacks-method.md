---
title: ICorDebugController::HasQueuedCallbacks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: c33193bd64030852441c7ca60cee4a000b09156c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788914"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks – metoda
Získá hodnotu, která označuje, zda jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThread`  
 pro Ukazatel na objekt "ICorDebugThread", který představuje vlákno.  
  
 `pbQueued`  
 mimo Ukazatel na hodnotu, která je `true`, pokud jsou pro zadané vlákno aktuálně zařazena všechna spravovaná zpětná volání. v opačném případě `false`.  
  
 Pokud je pro parametr `pThread` zadána hodnota null, `HasQueuedCallbacks` vrátí `true`, pokud jsou aktuálně spravovaná zpětná volání zařazena do fronty pro jakékoli vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Zpětná volání budou odeslána po jednom, pokaždé, když se zavolá [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) . Ladicí program může tento příznak kontrolovat, pokud chce ohlásit více událostí ladění, ke kterým dochází současně.  
  
 Když jsou události ladění zařazeny do fronty, již byly k dispozici, takže ladicí program musí celou frontu vyprázdnit, aby bylo zajištěno, že je stav laděného procesu. (Zavoláním `ICorDebugController::Continue` vyprázdní frontu.) Pokud například fronta obsahuje dvě události ladění ve vlákně *x*a ladicí program pozastaví vlákno *x* po první události ladění a poté zavolá `ICorDebugController::Continue`, bude druhá událost ladění pro vlákno *x* odeslána, i když bylo vlákno pozastaveno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
