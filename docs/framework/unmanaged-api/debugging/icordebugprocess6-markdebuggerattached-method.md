---
title: ICorDebugProcess6::MarkDebuggerAttached – metoda
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: 48bab20a71144b28f24951556eb36210d7b6aebf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123436"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached – metoda
Změní vnitřní stav laděného objektu tak, aby metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> v knihovně tříd .NET Framework vrátila `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`, zda by metoda <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> měla značit, že je připojen ladicí program. `false` jinak.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vracet hodnoty uvedené v následující tabulce.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Laděného procesu se úspěšně aktualizoval.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Sestavení, které obsahuje metodu <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>, není načteno nebo došlo k nějaké jiné chybě, například chybějící metadata, brání jejímu rozpoznání.<br /><br /> Tato chyba je běžná a neškodná. Metodu byste měli zavolat znovu, až se načtou další sestavení.|  
|Jiné neúspěšné `HRESULT` hodnoty.|Jiné hodnoty nejspíš naznačují, že se nechovají ladicí program nebo komponenty kompilátoru.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
