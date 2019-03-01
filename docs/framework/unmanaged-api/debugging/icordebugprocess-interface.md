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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dc732a8e3419a7ca42f5180d1bd32128ec33417
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967513"
---
# <a name="icordebugprocess-interface"></a>ICorDebugProcess – rozhraní
Představuje proces, který spouští spravovaný kód. Toto rozhraní je podtřídou třídy icordebugcontroller –.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Vymaže aktuální nespravované výjimky na dané vlákno.|  
|[EnableLogMessages – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Povolí nebo zakáže zasílání zpráv protokolu v ladicím programu.|  
|[EnumerateAppDomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Vytvoří výčet všech doménách aplikace v procesu.|  
|[EnumerateObjects – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Není implementováno.|  
|[GetHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Získá popisovač procesu.|  
|[GetHelperThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Získá ID vlákna operačního systému (OS) pro interní pomocné vlákno ladicího programu.|  
|[GetID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Získá ID operačního systému (OS) procesu.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Není implementováno.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Získá ID instance icordebugthread –, který má zadaný vlákna operačního systému|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Získá kontext pro dané vlákno.|  
|[IsOSSuspended – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Určuje, zda vlákna se pozastavilo, v důsledku ukončení procesu ladicího programu.|  
|[IsTransitionStub – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Určuje, zda je adresa uvnitř zástupnou proceduru, která způsobí, že s přechodem na spravovaný kód.|  
|[ModifyLogSwitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Nastaví úroveň závažnosti přepínače zadaný protokol.|  
|[ReadMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Přečte paměti z procesu.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Nastaví kontext pro dané vlákno.|  
|[ThreadForFiberCookie – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Zastaralé|  
|[WriteMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapíše data do oblasti paměti v procesu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
