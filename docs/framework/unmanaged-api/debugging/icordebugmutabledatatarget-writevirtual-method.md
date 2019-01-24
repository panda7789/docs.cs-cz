---
title: ICorDebugMutableDataTarget::WriteVirtual – metoda
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0f07e02ee92fda772a44fe235c3dcb414882bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495965"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual – metoda
Zapíše paměti do adresového prostoru cílového procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adresa, ve kterém se má zapsat obsah `pBuffer`.  
  
 `pBuffer`  
 [in] Ukazatel na bajtové pole obsahující bajty k zápisu.  
  
 `address`  
 [in] Počet bajtů v `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` na úspěch, nebo jakékoli jiné `HRESULT` při selhání.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nelze zapsány všechny bajty, beze změny všechny bajty v adresním prostoru cílového selže volání metody. (V opačném případě Cílem by být v nekonzistentním stavu, která provádí další ladění nespolehlivé.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
