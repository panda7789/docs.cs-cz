---
title: ICorDebugManagedCallback2::MDANotification – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208522"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification – metoda
Poskytuje oznámení o tom, že provádění kódu zjistilo v aplikaci, která je laděna, pomocníka spravovaného ladění (MDA).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pController`  
 pro Ukazatel na rozhraní ICorDebugController, které zpřístupňuje proces nebo doménu aplikace, ve které došlo k MDA.  
  
 Ladicí program by neměl dělat žádné předpoklady o tom, zda je kontroler nebo doména aplikace, i když se může vždy dotázat na rozhraní, aby bylo možné provést určení.  
  
 `pThread`  
 pro Ukazatel na rozhraní ICorDebugThread, které zveřejňuje spravované vlákno, na kterém došlo k události ladění.  
  
 Pokud k MDA došlo na nespravovaném vlákně, hodnota `pThread` bude null.  
  
 Musíte získat ID vlákna operačního systému (OS) z samotného objektu MDA.  
  
 `pMDA`  
 pro Ukazatel na rozhraní [ICorDebugMDA](icordebugmda-interface.md) , které zpřístupňuje informace MDA.  
  
## <a name="remarks"></a>Poznámky  
 MDA je heuristické upozornění a nevyžaduje žádnou explicitní akci ladicího programu s výjimkou volání [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) pro pokračování v provádění aplikace, která se právě ladí.  
  
 Modul CLR (Common Language Runtime) může určit, které MDA jsou vyvolány a která data jsou v jakémkoli okamžiku v daném bodě. Proto by ladicí program neměl vytvářet žádné funkce vyžadující konkrétní vzory MDA.  
  
 MDA se může zařadit do fronty a aktivovat krátce po zjištění MDA. K tomu může dojít v případě, že modul runtime potřebuje počkat, dokud nedosáhne bezpečného bodu pro vypálení služby MDA, namísto toho, aby se při jeho výskytu neiniciovala operace MDA. Také to znamená, že modul runtime může v jedné sadě zpětných volání ve frontě aktivovat určitý počet MDA (podobně jako operace "připojit").  
  
 Ladicí program by měl vydat odkaz na `ICorDebugMDA` instanci hned po návratu ze `MDANotification` zpětného volání, aby mohl modul CLR recyklovat paměť spotřebovaná pomocí MDA. Uvolnění instance může zlepšit výkon, pokud se právě MDA spousta.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
