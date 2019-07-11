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
ms.openlocfilehash: 96e63d121bb64fd1aa6433881f7806b5c4058115
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773996"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 – metoda
Získá velikost v bajtech, to [icordebugvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pSize  
 [out] Ukazatel na velikost v bajtech tohoto objektu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud tato hodnota typu je odkazový typ, vrátí tato metoda velikosti ukazatele, nikoli velikost objektu.  
  
 `ICorDebugValue3::GetSize` Metoda se liší od [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metoda v typu jeho výstupní parametr. V [icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), je výstupní parametr `ULONG32`; v `ICorDebugValue3::GetSize`, jde `ULONG64`. Díky tomu [icordebugvalue3 –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) rozhraní oznamuje velikost pole, které je větší než 2 GB.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugValue3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
