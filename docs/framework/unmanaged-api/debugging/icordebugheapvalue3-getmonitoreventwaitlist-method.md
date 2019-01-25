---
title: ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27815cf8cb7fdcd1c01f26391c317d52bbb388ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628510"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí se zámkem monitorování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 [out] Icordebugthreadenum – enumerátor, který poskytuje seřazený seznam vláken.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Seznam není prázdný.|  
|S_FALSE|Seznam je prázdný.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 První vlákno v seznamu je první vlákno, které se vydal další volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Další vlákno v seznamu je vydána následující volání a tak dále.  
  
 Pokud seznam není prázdný, tato metoda vrátí hodnotu S_OK. Pokud je seznam prázdný, vrátí metoda S_FALSE; v tomto případě je stále platné, výčtu, i když je prázdný.  
  
 V obou případech rozhraní výčtu je použitelné pouze po dobu trvání aktuálního stavu synchronizovaná. Však rozhraní vlákna distribuován z něj platí až do ukončení vlákna.  
  
 Pokud `ppThreadEnum` není platný ukazatel, výsledek nedefinován.  
  
 Pokud dojde k chybě, takže ji nelze určit, které případně vlákna čekají na monitorování, metoda vrátí HRESULT označující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
