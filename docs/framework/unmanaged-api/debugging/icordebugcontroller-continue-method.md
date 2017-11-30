---
title: "ICorDebugController::Continue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 93fc138b8610d252be5c3ca3821bb1d41c5ac6ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 `Continue`pokračuje v procesu po volání `ICorDebugController::Stop` metoda.  
  
 Při provádění modulu ladění ve smíšeném režimu, nevolejte `Continue` na Win32 událostí vláken, pokud jsou pokračováním z out-of-band události.  
  
 *Integrované událostí* spravované události nebo normální nespravované událostí, během které ladicí program podporuje interakci s spravované stavu procesu. V takovém případě obdrží ladicí program [icordebugunmanagedcallback::debugevent –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) zpětné volání s jeho `fOutOfBand` parametr nastaven na `false`.  
  
 *Out-of-band událostí* je událost nespravované, během kterého není možné interakci s spravované stav procesu, když je ukončen z důvodu události. V takovém případě obdrží ladicí program `ICorDebugUnmanagedCallback::DebugEvent` zpětné volání s jeho `fOutOfBand` parametr nastaven na `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
