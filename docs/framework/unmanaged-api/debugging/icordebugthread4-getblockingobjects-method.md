---
title: "ICorDebugThread4::GetBlockingObjects – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006535885868ef2778146f86e5395ea1f7605d6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects – metoda
Poskytuje seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) vláken struktury, které poskytují informace o blokování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 [out] Ukazatel na seřazený výčet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.  
  
## <a name="remarks"></a>Poznámky  
 První element ve vráceném výčtu odpovídá na první strukturu, která blokuje vlákno. Druhý prvkem odpovídá blokování položku, která je došlo při spouštění volání asynchronní procedury (APC), pokud je blokováno v prvním a tak dále.  
  
 Výčet je platný pouze po dobu trvání aktuálního stavu synchronizovaná.  
  
 Tato metoda musí být volána při ladění je ve stavu synchronizovaná.  
  
 Pokud `ppBlockingObjectEnum` není platný ukazatel, výsledkem nedefinovaný.  
  
 Pokud vlákno je blokovaný a nelze určit chyba, vrátí metoda HRESULT označující selhání; v opačném případě vrátí S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugThread4 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
