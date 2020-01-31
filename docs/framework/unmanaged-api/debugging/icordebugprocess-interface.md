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
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792595"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess – rozhraní
Představuje proces, který spouští spravovaný kód. Toto rozhraní je podtřídou třídy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](icordebugprocess-clearcurrentexception-method.md)|Vymaže aktuální nespravovanou výjimku na daném vlákně.|  
|[EnableLogMessages – metoda](icordebugprocess-enablelogmessages-method.md)|Povolí nebo zakáže odesílání zpráv protokolu do ladicího programu.|  
|[EnumerateAppDomains – metoda](icordebugprocess-enumerateappdomains-method.md)|Vytvoří výčet všech aplikačních domén v procesu.|  
|[EnumerateObjects – metoda](icordebugprocess-enumerateobjects-method.md)|Není implementováno.|  
|[GetHandle – metoda](icordebugprocess-gethandle-method.md)|Získá popisovač procesu.|  
|[GetHelperThreadID – metoda](icordebugprocess-gethelperthreadid-method.md)|Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.|  
|[GetID – metoda](icordebugprocess-getid-method.md)|Získá ID operačního systému (OS) procesu.|  
|[GetObject – metoda](icordebugprocess-getobject-method.md)|Není implementováno.|  
|[GetThread – metoda](icordebugprocess-getthread-method.md)|Získá instanci ICorDebugThread, která má zadané ID vlákna operačního systému.|  
|[GetThreadContext – metoda](icordebugprocess-getthreadcontext-method.md)|Získá kontext pro dané vlákno.|  
|[IsOSSuspended – metoda](icordebugprocess-isossuspended-method.md)|Určuje, zda bylo vlákno pozastaveno v důsledku zastavení procesu ladicího programu.|  
|[IsTransitionStub – metoda](icordebugprocess-istransitionstub-method.md)|Určuje, zda je adresa uvnitř zástupné procedury, která způsobí přechod ke spravovanému kódu.|  
|[ModifyLogSwitch – metoda](icordebugprocess-modifylogswitch-method.md)|Nastaví úroveň závažnosti určeného přepínače protokolu.|  
|[ReadMemory – metoda](icordebugprocess-readmemory-method.md)|Přečte z procesu paměť.|  
|[SetThreadContext – metoda](icordebugprocess-setthreadcontext-method.md)|Nastaví kontext pro dané vlákno.|  
|[ThreadForFiberCookie – metoda](icordebugprocess-threadforfibercookie-method.md)|Zastaralé|  
|[WriteMemory – metoda](icordebugprocess-writememory-method.md)|Zapisuje data do oblasti paměti v procesu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](icordebug-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
