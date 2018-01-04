---
title: "ICorDebugMutableDataTarget::WriteVirtual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 303c5737ebd241b8f2f756de0ed5426787de3bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual – metoda
Zapíše paměti do adresního prostoru procesu cíl.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [v] Adresa, kam chcete zapisovat obsah `pBuffer`.  
  
 `pBuffer`  
 [v] Ukazatel na bajtové pole obsahující bajty k zápisu.  
  
 `address`  
 [v] Počet bajtů v `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`na úspěch nebo jakékoliv `HRESULT` při selhání.  
  
## <a name="remarks"></a>Poznámky  
 Pokud žádné bajtů nelze zapsat, aniž byste museli měnit žádné bajtů v adresním prostoru cíl selže volání metody. (Jinak, cíl by být v nekonzistentním stavu, který vytvoří další ladění nespolehlivé.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
