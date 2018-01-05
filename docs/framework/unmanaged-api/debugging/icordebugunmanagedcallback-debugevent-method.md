---
title: "ICorDebugUnmanagedCallback::DebugEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent – metoda
Upozorní ladicí program, že nativní událostí je aktivován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 [v] Ukazatel na nativní událostí.  
  
 `fOutOfBand`  
 [v] `true`, pokud interakci s stavu spravovaného procesu není možné po nespravované události dojde, dokud volání ladicí program [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md), jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je vlákno laděné Win32 vlákno, nepoužívejte žádné členy Win32 ladění v rozhraní. Můžete volat `ICorDebugController::Continue` pouze ve vlákně Win32 a pouze v případě, že budete pokračovat po out-of-band událost.  
  
 `DebugEvent` Zpětného volání nedodrží standardní pravidla pro zpětných volání. Při volání `DebugEvent`, proces bude v nezpracovaná, OS-debug zastaveno stavu. Proces se nebudou synchronizovat. Zadá automaticky synchronizovaného stavu, když je potřeba splnit požadavky na informace o spravovaného kódu, což může vést k jiné vnořené `DebugEvent` zpětných volání.  
  
 Volání [icordebugprocess::clearcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na procesu, ignorovat událost výjimky před pokračováním procesu. Voláním této metody odešle DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED u požadavku pokračovat a automaticky vymaže krokování výjimek a out-of-band zarážky. Out-of-band události můžou mít kdykoli, i v případě, že laděné aplikace se zobrazí ukončeno, a když nevyřízené události integrované již existuje.  
  
 V rozhraní .NET Framework verze 2.0 by měly ladicího programu okamžitě pokračovat po zarážku – out-of-band událost. Ladicí program by měl používat [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) a [icordebugprocess2::clearunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody pro přidání a odebrání zarážky. Tyto metody automaticky přeskočí přes všechny out-of-band zarážky. Proto pouze out-of-band zarážky, které získat odeslaných by měla být nezpracovaná zarážky, které jsou již v datovém proudu instrukce, jako je například volání Win32 `DebugBreak` funkce. Nepokoušejte se použít `ICorDebugProcess::ClearCurrentException`, [icordebugprocess::getthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess::setthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), nebo jakékoli jiné člen [rozhraní API pro ladění](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugUnmanagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
