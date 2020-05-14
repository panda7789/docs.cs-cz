---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396427"
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
 `S_OK`Pokud se unwind úspěšně nastalo, nebo `CORDBG_S_AT_END_OF_STACK` Pokud se unwind nedá dokončit, protože neexistují žádné další snímky.  
  
 Pokud se vrátí neúspěšná hodnota HRESULT, vrátí rozhraní API ICorDebug `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Poznámky  
 Zásobník prohlížeč by měl zajistit, že předává průběh vpřed, takže nakonec volání `Next` vrátí HRESULT nebo `CORDBG_S_AT_END_OF_STACK` . Vrácení bez `S_OK` omezení může způsobit nekonečnou smyčku.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMemoryBuffer – rozhraní](icordebugmemorybuffer-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
