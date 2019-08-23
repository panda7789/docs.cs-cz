---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967923"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next – metoda
Přejde do kontextu volajícího.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud se unwind úspěšně nastalo, `CORDBG_S_AT_END_OF_STACK` nebo pokud se unwind nedá dokončit, protože neexistují žádné další snímky.  
  
 Pokud se vrátí neúspěšná hodnota HRESULT, vrátí `CORDBG_E_DATA_TARGET_ERROR`rozhraní API ICorDebug.  
  
## <a name="remarks"></a>Poznámky  
 Zásobník prohlížeč by měl zajistit, že předává průběh vpřed, takže nakonec volání `Next` vrátí HRESULT nebo. `CORDBG_S_AT_END_OF_STACK` Vrácení `S_OK` bez omezení může způsobit nekonečnou smyčku.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
