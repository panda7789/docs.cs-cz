---
title: "ICorDebugManagedCallback2::MDANotification – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.MDANotification
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aeddab575f6667dbd27ab3474ae9c6e00dd05750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification – metoda
Poskytuje oznámení, že provádění kódu se vyskytla spravované ladění pomocníka (MDA) v aplikaci, která je právě laděn.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pController`  
 [v] Ukazatel na ICorDebugController rozhraní, které zpřístupňuje proces nebo doménu aplikace, ve kterém MDA došlo.  
  
 Ladicí program neprovádějte žádné předpoklady o tom, zda je řadič procesu nebo doménu aplikace, i když může se vždy dotázat rozhraní pro určení.  
  
 `pThread`  
 [v] Ukazatel na ICorDebugThread rozhraní, které vystavuje spravovaných vláken, na kterém došlo k události ladění.  
  
 Pokud MDA došlo k chybě na nespravované vláken, hodnota `pThread` bude mít hodnotu null.  
  
 ID vlákna operační systém (OS), musíte si z samotného objektu (mda).  
  
 `pMDA`  
 [v] Ukazatel na [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) rozhraní, která zveřejňuje informace (mda).  
  
## <a name="remarks"></a>Poznámky  
 MDA je Heuristická upozornění a nevyžaduje žádné explicitní ladicí program akce s výjimkou volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) Chcete-li pokračovat v provádění aplikace, která je právě laděn.  
  
 Modul CLR (CLR) můžete určit, který při vyvolání mda a data, která je v jakékoli dané MDA v libovolném bodě. Proto by nemělo ladicí programy sestavení žádné funkce, které vyžadují určité vzory (mda).  
  
 Mda mohou být zařazeny do fronty a aktivováno krátce po narazí (mda). Toto může nastat, pokud modul runtime musí počkat, dokud nebude dosaženo bod bezpečné pro ohlásí MDA, místo aktivuje MDA, když se zjistí. Taky to znamená, že modul runtime může aktivovat počet mda v jedné sadě zařazených do fronty zpětných volání (podobně jako událost operace "připojit").  
  
 Ladicí program by měl verze odkaz na `ICorDebugMDA` instance ihned po vrácení z `MDANotification` zpětné volání, chcete-li povolit modul CLR recyklace paměťové nároky (mda). Uvolnění instance může zvýšit výkon, pokud se aktivuje mnoho mda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [ICorDebugManagedCallback2 – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
