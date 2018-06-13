---
title: ICorDebugProcess Interface1
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
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423166"
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
Představuje proces, který spouští spravovaný kód. Toto rozhraní je podtřídou třídy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ClearCurrentException – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Vymaže aktuální nespravované výjimky na dané vlákno.|  
|[EnableLogMessages – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Povolí nebo zakáže odesílání zpráv protokolu ladicího programu.|  
|[EnumerateAppDomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Zobrazí všechny domény aplikace v procesu.|  
|[EnumerateObjects – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Není implementováno.|  
|[GetHandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Získá popisovač pro proces.|  
|[GetHelperThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Získá ID vlákna operační systém (OS) pro vlákno interní pomocná ladicího programu.|  
|[GetID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Získá ID operační systém (OS) procesu.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Není implementováno.|  
|[GetThread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Získá ID instance ICorDebugThread, který má zadaný vlákno operačního systému|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Získá kontext pro dané vlákno.|  
|[IsOSSuspended – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Určuje, zda bylo pozastaveno vlákno v důsledku ladicí program ukončení procesu.|  
|[IsTransitionStub – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Určuje, zda adresu uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.|  
|[ModifyLogSwitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Nastaví úroveň závažnosti zadaného protokolu přepínače.|  
|[ReadMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Přečte paměti z procesu.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Nastaví kontext pro dané vlákno.|  
|[ThreadForFiberCookie – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Zastaralé|  
|[WriteMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje data do oblast paměti v procesu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
