---
title: ICorDebugController::Continue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f448a0383d3ad121cbddb59e13acef46a336261
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485730"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue – metoda
Pokračuje v provádění spravovaná vlákna po volání [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsOutOfBand`  
 [in] Nastavte na `true` Pokud budete pokračovat z události out-of-band; v opačném případě nastavte na `false`.  
  
## <a name="remarks"></a>Poznámky  
 `Continue` pokračuje v procesu po volání `ICorDebugController::Stop` metody.  
  
 Při ladění ve smíšeném režimu, nevolejte `Continue` na Win32 události vlákna, pokud se dál pokračuje z out-of-band události.  
  
 *Integrovaných událostí* je spravovaná událost nebo normální nespravované události, během které ladicí program podporuje interakci s spravovaného stavu zpracování. V takovém případě ladicí program přijímá [icordebugunmanagedcallback::debugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) zpětného volání s jeho `fOutOfBand` parametr nastaven na `false`.  
  
 *Out-of-band události* nespravované události během které je možné interakce s spravované stav procesu, zatímco je ukončen z důvodu události. V takovém případě ladicí program přijímá `ICorDebugUnmanagedCallback::DebugEvent` zpětného volání s jeho `fOutOfBand` parametr nastaven na `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

