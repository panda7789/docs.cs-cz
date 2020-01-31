---
title: 'ICorDebugVirtualUnwinder:: Next – metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790821"
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
 `S_OK`, zda došlo k rewindu úspěšně, nebo `CORDBG_S_AT_END_OF_STACK`, Pokud unwind nelze dokončit, protože neexistují žádné další snímky.  
  
 Pokud je vrácena neúspěšná hodnota HRESULT, vrátí rozhraní API ICorDebug `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
 Prohlížeč zásobníku by měl zajistit, že bude předávat pokrok, aby nakonec volání `Next` vrátilo neúspěch HRESULT nebo `CORDBG_S_AT_END_OF_STACK`. Vrácení `S_OK` bez omezení může způsobit nekonečnou smyčku.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMemoryBuffer – rozhraní](icordebugmemorybuffer-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
