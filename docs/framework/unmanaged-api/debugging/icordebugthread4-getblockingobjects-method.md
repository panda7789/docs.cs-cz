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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca6b057225ce4d453cd156bea9f941369586cd81
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473758"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects – metoda
Poskytuje seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vlákna struktury, které poskytují informace o blokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Ukazatel na seřazený výčet [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="remarks"></a>Poznámky  
 První prvek ve vrácené výčtu odpovídá první strukturu, která blokuje vlákno. Druhý prvek odpovídá blokující položkou, na kterou narazí při spouštění volání rozhraní asynchronní procedury (APC) při zablokování prvního a tak dále.  
  
 Výčet je platný pouze po dobu trvání aktuálního stavu synchronizovaná.  
  
 Tato metoda musí být volána, když laděný proces je ve stavu synchronizovaná.  
  
 Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledek nedefinován.  
  
 Pokud je vlákno blokované a chyba nelze určit, že vrátí tato metoda hodnotu HRESULT označující selhání; v opačném případě vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
