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
ms.openlocfilehash: cb52150a17c9ec8f4bbc25c13b85bce56b221eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791196"
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
 [in] `true`, pokud interakce se stavem spravovaného procesu není nemožné po výskytu nespravované události, dokud ladicí program nevolá [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud vlákno, které je laděno, je vlákno Win32, nepoužívejte žádné členy ladicího rozhraní Win32. Můžete volat `ICorDebugController::Continue` pouze ve vlákně Win32 a pouze v případě, že budete pokračovat po událostech mimo pásmo.  
  
 Zpětné volání `DebugEvent` nedodržuje standardní pravidla pro zpětná volání. Když zavoláte `DebugEvent`, proces bude ve stavu raw, zastaveno a ladění operačního systému. Proces nebude synchronizován. Automaticky zadá synchronizovaný stav, pokud je to nutné k tomu, aby splňoval požadavky na informace o spravovaném kódu, což může vést k dalším vnořeným zpětným voláním `DebugEvent`.  
  
 Před pokračováním procesu zavolejte [ICorDebugProcess:: ClearCurrentException –](icordebugprocess-clearcurrentexception-method.md) na proces, aby se ignorovala událost výjimky. Volání této metody odesílá DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED v žádosti o pokračování a automaticky vymaže zarážky mimo pásmo a výjimky s jedním krokem. Události mimo pásmo můžou přijít kdykoli, a to i v případě, že se vyladěná aplikace zastaví a když už existuje zbývající událost v pásmu.  
  
 V .NET Framework verze 2,0 by měl ladicí program hned pokračovat v minulosti událost zarážky mimo pásmo. Ladicí program by měl používat metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md) a [ICorDebugProcess2:: ClearUnmanagedBreakpoint –](icordebugprocess2-clearunmanagedbreakpoint-method.md) k přidávání a odebírání zarážek. Tyto metody přeskočí všechny zarážky mimo pásmo automaticky. Proto musí být pouze nezpracované zarážky mimo pásmo, které byly odeslány, nezpracované zarážky, které jsou již v datovém proudu instrukcí, například volání funkce Win32 `DebugBreak`. Nepokoušejte se používat `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: GetThreadContext –](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext –](icordebugprocess-setthreadcontext-method.md)nebo jakéhokoli jiného člena [rozhraní API pro ladění](index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugUnmanagedCallback – rozhraní](icordebugunmanagedcallback-interface.md)
