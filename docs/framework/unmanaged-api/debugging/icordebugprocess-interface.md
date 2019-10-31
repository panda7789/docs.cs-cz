---
title: ICorDebugProcess – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: 393ac8c119f111b645e7ccdb6ea94efee7207fa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128797"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess – rozhraní
Představuje proces, který spouští spravovaný kód. Toto rozhraní je podtřídou třídy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Vymaže aktuální nespravovanou výjimku na daném vlákně.|  
|[EnableLogMessages – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Povolí nebo zakáže odesílání zpráv protokolu do ladicího programu.|  
|[EnumerateAppDomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Vytvoří výčet všech aplikačních domén v procesu.|  
|[EnumerateObjects – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Není implementováno.|  
|[GetHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Získá popisovač procesu.|  
|[GetHelperThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.|  
|[GetID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Získá ID operačního systému (OS) procesu.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Není implementováno.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Získá instanci ICorDebugThread, která má zadané ID vlákna operačního systému.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Získá kontext pro dané vlákno.|  
|[IsOSSuspended – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Určuje, zda bylo vlákno pozastaveno v důsledku zastavení procesu ladicího programu.|  
|[IsTransitionStub – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Určuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.|  
|[ModifyLogSwitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Nastaví úroveň závažnosti určeného přepínače protokolu.|  
|[ReadMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Přečte z procesu paměť.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Nastaví kontext pro dané vlákno.|  
|[ThreadForFiberCookie – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Zastaralé|  
|[WriteMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje data do oblasti paměti v procesu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
