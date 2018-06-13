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
ms.openlocfilehash: 529a65285203ac831e1bcab9dc1bea69ac28a282
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412562"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue – metoda
Pokračuje v provádění spravovaných vláknech po volání [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fIsOutOfBand`  
 [v] Nastavte na `true` Pokud budete pokračovat z události out-of-band; jinak hodnota nastavena na `false`.  
  
## <a name="remarks"></a>Poznámky  
 `Continue` pokračuje v procesu po volání `ICorDebugController::Stop` metoda.  
  
 Při provádění modulu ladění ve smíšeném režimu, nevolejte `Continue` na Win32 událostí vláken, pokud jsou pokračováním z out-of-band události.  
  
 *Integrované událostí* spravované události nebo normální nespravované událostí, během které ladicí program podporuje interakci s spravované stavu procesu. V takovém případě obdrží ladicí program [icordebugunmanagedcallback::debugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) zpětné volání s jeho `fOutOfBand` parametr nastaven na `false`.  
  
 *Out-of-band událostí* je událost nespravované, během kterého není možné interakci s spravované stav procesu, když je ukončen z důvodu události. V takovém případě obdrží ladicí program `ICorDebugUnmanagedCallback::DebugEvent` zpětné volání s jeho `fOutOfBand` parametr nastaven na `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
