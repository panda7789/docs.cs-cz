---
title: 'ICorDebugMutableDataTarget:: Writevirtual – – metoda'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792836"
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

- [ICorDebugMutableDataTarget – rozhraní](icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
