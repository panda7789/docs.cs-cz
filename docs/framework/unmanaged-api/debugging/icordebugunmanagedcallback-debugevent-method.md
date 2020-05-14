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
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397195"
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
 [in] `true` , pokud interakce se stavem spravovaného procesu není nemožné po výskytu nespravované události, dokud ladicí program nevolá [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); jinak `false` .  
  
## <a name="remarks"></a>Poznámky  
 Pokud vlákno, které je laděno, je vlákno Win32, nepoužívejte žádné členy ladicího rozhraní Win32. Můžete zavolat `ICorDebugController::Continue` pouze na vlákno Win32 a jenom v případě, že budete pokračovat po událostech mimo pásmo.  
  
 `DebugEvent`Zpětné volání nedodržuje standardní pravidla pro zpětná volání. Když zavoláte `DebugEvent` , proces bude ve stavu raw, zastaveno a ladění operačního systému. Proces nebude synchronizován. Automaticky zadá synchronizovaný stav, pokud je to nutné k tomu, aby splňoval požadavky na informace o spravovaném kódu, což může vést k dalším vnořeným `DebugEvent` zpětným voláním.  
  
 Před pokračováním procesu zavolejte [ICorDebugProcess:: ClearCurrentException –](icordebugprocess-clearcurrentexception-method.md) na proces, aby se ignorovala událost výjimky. Volání této metody odesílá DBG_CONTINUE místo DBG_EXCEPTION_NOT_HANDLED v žádosti o pokračování a automaticky vymaže zarážky mimo pásmo a výjimky s jedním krokem. Události mimo pásmo můžou přijít kdykoli, a to i v případě, že se vyladěná aplikace zastaví a když už existuje zbývající událost v pásmu.  
  
 V .NET Framework verze 2,0 by měl ladicí program hned pokračovat v minulosti událost zarážky mimo pásmo. Ladicí program by měl používat metody [ICorDebugProcess2:: SetUnmanagedBreakpoint –](icordebugprocess2-setunmanagedbreakpoint-method.md) a [ICorDebugProcess2:: ClearUnmanagedBreakpoint –](icordebugprocess2-clearunmanagedbreakpoint-method.md) k přidávání a odebírání zarážek. Tyto metody přeskočí všechny zarážky mimo pásmo automaticky. Proto musí být pouze nezpracované zarážky mimo pásmo, které byly odeslány, nezpracované zarážky, které jsou již v datovém proudu instrukcí, například volání `DebugBreak` funkce Win32. Nepokoušejte se použít `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess:: GetThreadContext –](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext –](icordebugprocess-setthreadcontext-method.md)nebo jakýkoli jiný člen [rozhraní API pro ladění](index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugUnmanagedCallback – rozhraní](icordebugunmanagedcallback-interface.md)
