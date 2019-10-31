---
title: 'ICorDebugMutableDataTarget:: Writevirtual – – metoda'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 5947caa8dfb97574bb4b3c5634d962df153211c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132683"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget:: Writevirtual – – metoda
Zapíše paměť do cílového adresního prostoru procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 pro Adresa, na které se má zapisovat obsah `pBuffer`.  
  
 `pBuffer`  
 pro Ukazatel na pole bajtů obsahující bajty, které mají být zapsány.  
  
 `address`  
 pro Počet bajtů v `pBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` při úspěchu nebo jakékoli jiné `HRESULT` při selhání.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nemůžete zapsat libovolné bajty, volání metody se nepovede bez změny jakýchkoli bajtů v cílovém adresním prostoru. (Jinak by byl cíl v nekonzistentním stavu, který umožňuje další ladění nespolehlivě.)  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
