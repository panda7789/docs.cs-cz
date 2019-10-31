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
ms.openlocfilehash: 2d865f837d38894e8449af671e2d12e7676dd040
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129133"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent – metoda
Oznamuje ladicímu programu, že byla vyvolána nativní událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDebugEvent`  
 pro Ukazatel na nativní událost.  
  
 `fOutOfBand`  
 [in] `true`, pokud interakce se stavem spravovaného procesu není nemožné po výskytu nespravované události, dokud ladicí program nevolá [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud vlákno, které je laděno, je vlákno Win32, nepoužívejte žádné členy ladicího rozhraní Win32. Můžete volat `ICorDebugController::Continue` pouze ve vlákně Win32 a pouze v případě, že budete pokračovat po událostech mimo pásmo.  
  
 Zpětné volání `DebugEvent` nedodržuje standardní pravidla pro zpětná volání. Když zavoláte `DebugEvent`, proces bude ve stavu raw, zastaveno a ladění operačního systému. Proces nebude synchronizován. Automaticky zadá synchronizovaný stav, pokud je to nutné k tomu, aby splňoval požadavky na informace o spravovaném kódu, což může vést k dalším vnořeným zpětným voláním `DebugEvent`.  
  
 Před pokračováním procesu zavolejte [ICorDebugProcess:: ClearCurrentException –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) na proces, aby se ignorovala událost výjimky. Volání této metody pošle DBG_CONTINUE namísto DBG_EXCEPTION_NOT_HANDLED na žádost o pokračování a automaticky smaže zarážky mimo pásmo a výjimky s jedním krokem. Události mimo pásmo můžou přijít kdykoli, a to i v případě, že se vyladěná aplikace zastaví a když už existuje zbývající událost v pásmu.  
  
 V .NET Framework verze 2,0 by měl ladicí program hned pokračovat v minulosti událost zarážky mimo pásmo. Ladicí program by měl používat metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) a [ICorDebugProcess2:: ClearUnmanagedBreakpoint –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) k přidávání a odebírání zarážek. Tyto metody přeskočí všechny zarážky mimo pásmo automaticky. Proto musí být pouze nezpracované zarážky mimo pásmo, které byly odeslány, nezpracované zarážky, které jsou již v datovém proudu instrukcí, například volání funkce Win32 `DebugBreak`. Nepokoušejte se používat `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)nebo jakéhokoli jiného člena [rozhraní API pro ladění](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugUnmanagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
