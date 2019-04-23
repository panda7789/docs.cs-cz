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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 425c606b1f340bbd49cfe3497d394d5ad0dd37a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133469"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification – metoda
Poskytuje oznámení, že spuštění kódu došlo k Pomocník spravovaného ladění (MDA) v aplikaci, která je právě laděna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pController`  
 [in] Ukazatel na icordebugcontroller – rozhraní, která zveřejňuje proces nebo doménu aplikace, ve kterém MDA došlo.  
  
 Ladicí program by neměla provést nevyvozujte předpoklady o tom, jestli je kontroler proces nebo doménu aplikace, i když ho vždy dotazování rozhraní pro určení.  
  
 `pThread`  
 [in] Ukazatel na icordebugthread – rozhraní, která zveřejňuje spravované vlákno, na kterém došlo k události ladění.  
  
 Pokud MDA došlo k chybě na nespravované vlákna, hodnota `pThread` bude mít hodnotu null.  
  
 ID vlákna operačního systému (OS) musí získat od samotného objektu MDA.  
  
 `pMDA`  
 [in] Ukazatel [icordebugmda –](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) rozhraní, které zveřejňuje informace o MDA.  
  
## <a name="remarks"></a>Poznámky  
 MDA heuristické upozornění a nevyžaduje žádnou akci explicitní ladicího programu s výjimkou volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pokračovat provádění aplikace, která je právě laděna.  
  
 Modul CLR (CLR) můžete určit, které jsou vyvolávány mda a která data se v jakékoli dané MDA v libovolném bodě. Proto by neměl ladicí programy sestavení všechny funkce, které vyžadují specifické vzory MDA.  
  
 Mda mohou být zařazeny do fronty a krátce po narazí MDA aktivuje. Může k tomu dojít, pokud modul runtime musí čekat, dokud nedosáhne bod bezpečné pro aktivaci MDA, místo spouštění MDA, pokud se setká. Také znamená, že modul runtime může vyvolat počet mda v jediné sady kontrolních zařazených do fronty zpětná volání (podobné události operace "připojit").  
  
 Ladicí program by měla uvolnit odkaz na `ICorDebugMDA` instance ihned po vrácení z `MDANotification` zpětné volání, chcete-li povolit modul CLR recyklace paměti používané MDA. Uvolnění instance může zvýšit výkon, pokud se ohlásí mnoho mda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
