---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList – metoda
Poskytuje seřazený seznam vláken, které jsou zařazeny do fronty na událost, která souvisí s monitorování zámku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 [out] ICorDebugThreadEnum enumerátor, který poskytuje seřazený seznam vláken.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|V seznamu není prázdná.|  
|S_FALSE|Seznam je prázdný.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 První vlákno v seznamu se první vlákno, které je publikována v rámci další volání <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Další vlákno v seznamu je vydala následující volání a tak dále.  
  
 Pokud v seznamu není prázdný, vrátí tato metoda S_OK. Pokud je seznam prázdný, vrátí metoda S_FALSE; v takovém případě je stále platný, výčtu, i když je prázdný.  
  
 V obou případech je rozhraní výčtu použitelné pouze po dobu trvání aktuálního stavu synchronizovaná. Vlákna rozhraní distribuován z něj jsou však platný až do konce vlákno.  
  
 Pokud `ppThreadEnum` není platný ukazatel, výsledkem nedefinovaný.  
  
 Pokud dojde k chybě tak, že nelze určit, která, pokud existuje, vláken, které čekají na monitorování, vrátí metoda HRESULT označující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
