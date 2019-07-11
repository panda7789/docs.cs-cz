---
title: ICorDebugUnmanagedCallback::DebugEvent – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c75e1844fca4e592faa924a55432dd42fa7355
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772617"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent – metoda
Upozorní ladicího programu, že nativní události byl aktivován.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 [in] Ukazatel na nativní události.  
  
 `fOutOfBand`  
 [in] `true`, pokud po výskytu nespravované události, až do volání ladicího programu není možné interakce s daným stavem spravovaného procesu [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Vlákno Win32 při ladění vlákna se nepoužívají žádné členy Win32 ladění v rozhraní. Můžete volat `ICorDebugController::Continue` pouze na vlákno Win32 a pouze v případě, že budete pokračovat minulé události out-of-band.  
  
 `DebugEvent` Zpětného volání nedodržuje standardní pravidla pro zpětná volání. Při volání `DebugEvent`, proces bude v nezpracovaná, operační systém ladění stavu Zastaveno. Proces se nebudou synchronizovat. Zadá automaticky synchronizované stavové, když je potřeba splnit požadavky na informace o spravovaného kódu, který může vést k jiné vnořené `DebugEvent` zpětná volání.  
  
 Volání [icordebugprocess::clearcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na postup ignorovat události výjimky před pokračováním procesu. Voláním této metody odesílá DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED v požadavku pokračovat a automaticky vymaže out-of-band zarážky a krokování výjimky. Out-of-band události můžou mít v každém okamžiku i v případě, že právě laděné aplikace, zobrazí se zastavila, a když nezpracovaných událostí ve vzdálené již existuje.  
  
 V rozhraní .NET Framework verze 2.0 by měl ladicí program okamžitě pokračovat po zarážku out-of-band událost. Ladicí program by měl používat [icordebugprocess2::setunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) a [icordebugprocess2::clearunmanagedbreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) metody pro přidání a odebrání zarážky. Tyto metody se přeskočit všechny zarážky out-of-band automaticky. Proto pouze out-of-band zarážek, které získáte odeslaných by měl být nezpracovaná zarážky, které jsou již ve službě stream instrukce, jako je například voláním rozhraní Win32 `DebugBreak` funkce. Nepokoušejte se použít `ICorDebugProcess::ClearCurrentException`, [icordebugprocess::getthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [icordebugprocess::setthreadcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), nebo libovolný jiný člen [ladění v rozhraní API](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugUnmanagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
