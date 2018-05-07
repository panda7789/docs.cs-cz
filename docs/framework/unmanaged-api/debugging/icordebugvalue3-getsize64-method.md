---
title: ICorDebugValue3::GetSize64 – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d3925741e9777e4fcd1752d8e24bf71ad1579f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 – metoda
Získá velikost v bajtech to [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pSize  
 [out] Ukazatel na velikost v bajtech tohoto objektu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je tato hodnota typ typu odkazu, tato metoda vrátí velikost ukazatele spíše než velikost objektu.  
  
 `ICorDebugValue3::GetSize` Metoda se liší od [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metoda v typu jeho výstupní parametr. V [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), je výstupní parametr `ULONG32`; v `ICorDebugValue3::GetSize`, je `ULONG64`. Díky tomu [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) rozhraní tak, aby odesílaly velikost pole, které překračují 2 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
