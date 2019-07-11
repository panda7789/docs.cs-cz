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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d17f51867b64780fca9b21c5f48c88db36343af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748781"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks – metoda
Získá hodnotu určující, zda všechny spravované zpětná volání jsou právě ve frontě pro zadaný podproces.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThread`  
 [in] Ukazatel na objekt "ICorDebugThread", který představuje vlákno.  
  
 `pbQueued`  
 [out] Ukazatel na hodnotu, která je `true` Pokud žádné spravované zpětná volání nejsou aktuálně ve frontě pro zadaný podproces; v opačném případě `false`.  
  
 Pokud je zadána hodnota null pro `pThread` parametr `HasQueuedCallbacks` vrátí `true` Pokud aktuálně spravované zpětná volání zařazených do fronty pro jakékoli vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Zpětná volání bude odbavované jeden po druhém, pokaždé, když [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volána. Ladicí program můžete zkontrolovat tento příznak, pokud chce sestavy více ladění události, které probíhají souběžně.  
  
 Při ladění událostí se zařadí do fronty, jsou již došlo, aby ladicí program musí vyprázdnit celá fronta opravdu o stavu laděného procesu. (Volání `ICorDebugController::Continue` k vyprázdnění fronty.) Například, pokud tato fronta obsahuje dvě ladění události na vlákně *X*, a ladicí program pozastaví vlákno *X* po první ladění události a poté zavolá `ICorDebugController::Continue`, druhá událost ladění pro vlákno *X* bude odeslána, i když je pozastavená vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
