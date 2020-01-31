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
ms.openlocfilehash: 8be7c0e32f6183deb354d8b3936ef55c2520fe9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788612"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock – metoda
Vrátí spravované vlákno, které vlastní zámek monitorování tohoto objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThread`  
 mimo Spravované vlákno, které pro tento objekt vlastní zámek monitoru.  
  
 `pAcquisitionCount`  
 mimo Počet, kolikrát by toto vlákno muselo uvolnit zámek předtím, než se vrátí k nevlastnictví.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|S_FALSE|Žádné spravované vlákno nevlastní na tomto objektu zámek monitorování.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Pokud spravované vlákno vlastní zámek monitoru u tohoto objektu:  
  
- Metoda vrací S_OK.  
  
- Objekt vlákna je platný, dokud vlákno neskončí.  
  
 Pokud žádné spravované vlákno nevlastní zámek monitoru u tohoto objektu, `ppThread` a `pAcquisitionCount` se nezměnily a metoda vrátí S_FALSE.  
  
 Pokud `ppThread` nebo `pAcquisitionCount` není platný ukazatel, výsledek není definován.  
  
 Pokud dojde k chybě, kterou nelze určit, která, pokud existuje, je vláknom zámku monitoru pro tento objekt, metoda vrátí hodnotu HRESULT, která označuje selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
