---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee526a79d89a9e4e3483daa07a512b6b7f920e70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
Představuje proces, který spouští spravovaný kód. Toto rozhraní je podtřídou třídy ICorDebugController.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clearcurrentexception – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|Vymaže aktuální nespravované výjimky na dané vlákno.|  
|[Enablelogmessages – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|Povolí nebo zakáže odesílání zpráv protokolu ladicího programu.|  
|[Enumerateappdomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|Zobrazí všechny domény aplikace v procesu.|  
|[Enumerateobjects – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|Není implementováno.|  
|[Gethandle – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|Získá popisovač pro proces.|  
|[Gethelperthreadid – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|Získá ID vlákna operační systém (OS) pro vlákno interní pomocná ladicího programu.|  
|[Getid – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|Získá ID operační systém (OS) procesu.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|Není implementováno.|  
|[Getthread – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|Získá ID instance ICorDebugThread, který má zadaný vlákno operačního systému|  
|[Getthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|Získá kontext pro dané vlákno.|  
|[Isossuspended – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|Určuje, zda bylo pozastaveno vlákno v důsledku ladicí program ukončení procesu.|  
|[Istransitionstub – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|Určuje, zda adresu uvnitř se zakázaným inzerováním, které způsobí přechod do spravovaného kódu.|  
|[Modifylogswitch – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|Nastaví úroveň závažnosti zadaného protokolu přepínače.|  
|[Readmemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|Přečte paměti z procesu.|  
|[Setthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|Nastaví kontext pro dané vlákno.|  
|[Threadforfibercookie – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|Zastaralé|  
|[Writememory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|Zapisuje data do oblast paměti v procesu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
