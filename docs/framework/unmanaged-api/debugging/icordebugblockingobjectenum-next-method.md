---
title: "ICorDebugBlockingObjectEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c05420a54d7a79198e235a39e578bedf296b4fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next – metoda
Získá zadaný počet [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty z výčtu, počínaje na aktuální pozici.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingOjbect values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet objektů pro načtení.  
  
 `values`  
 [out] Pole ukazatele na [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty.  
  
 `pceltFetched`  
 [out] Ukazatel na počet objektů, které byly načteny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|S_FALSE|`pceltFetched`není rovno `celt`.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda funguje jako typický COM enumerátor.  
  
 Vstupní pole hodnoty musí být aspoň o velikosti `celt`. Pole bude vyplněn buď Další `celt` hodnoty ve výčtu nebo s všechny zbývající hodnoty, pokud méně než `celt` zůstanou. Po návratu tato metoda `pceltFetched` bude vyplněn počet hodnot, které byly načteny. Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`, nebo pokud `pceltFetched` je neplatný ukazatel, výsledkem nedefinovaný.  
  
> [!NOTE]
>  I když [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktura není nutné uvolnit, rozhraní "ICorDebugValue" uvnitř této potřebuje k uvolnění.  
  
-  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
