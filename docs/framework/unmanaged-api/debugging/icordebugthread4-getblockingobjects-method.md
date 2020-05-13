---
title: ICorDebugThread4::GetBlockingObjects – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 366b5124cc66a4e9a1c3bd4e77f604f15ba8d8a8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379676"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects – metoda
Poskytuje seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) , které poskytují informace o blokování vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 mimo Ukazatel na seřazený výčet struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .  
  
## <a name="remarks"></a>Poznámky  
 První prvek vráceného výčtu odpovídá první struktuře, která blokuje vlákno. Druhý prvek odpovídá blokující položce, která se objevila při spuštění asynchronní procedury volání (APC) při zablokování v prvním, a tak dále.  
  
 Výčet je platný pouze po dobu trvání aktuálního synchronizovaného stavu.  
  
 Tato metoda musí být volána, když je laděného procesu v synchronizovaném stavu.  
  
 Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek není definován.  
  
 Pokud je vlákno blokované a chybu nelze určit, metoda vrátí hodnotu HRESULT, která označuje selhání. v opačném případě vrátí S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugThread4 – rozhraní](icordebugthread4-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
