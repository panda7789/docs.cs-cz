---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d3e10a3dbae0d1b790c0d80c9286affedaa4c8b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709140"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda
Vrátí spravované vlákno, který vlastní monitorování zámek na tomto objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Spravovaná vlákna, které vlastní monitorování zámek na tomto objektu.  
  
 `pAcquisitionCount`  
 [out] Počet pokusů, museli byste toto vlákno uvolní zámek před vrácením se bez přiřazeného vlastníka.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|S_FALSE|Žádné spravované vlákno vlastní monitorování zámek na tomto objektu.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Pokud spravované vlákno vlastní monitorování zámek na tomto objektu:  
  
-   Metoda vrátí hodnotu S_OK.  
  
-   Objekt vlákna je platná, dokud se vlákno ukončí.  
  
 Pokud žádné spravované vlákno vlastní monitorování zámek na tomto objektu `ppThread` a `pAcquisitionCount` jsou beze změny, a metoda vrátí S_FALSE.  
  
 Pokud `ppThread` nebo `pAcquisitionCount` není platný ukazatel, výsledek nedefinován.  
  
 Pokud dojde k chybě, takže ji nelze určit, který, pokud existuje, vlákno vlastní monitorování zámek na tomto objektu, metoda vrátí HRESULT označující selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
