---
title: ICorDebugProcess6::MarkDebuggerAttached – metoda
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c83d6e892b89e6e50779abf9a71a2cbe9093af2c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212842"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached – metoda
Změní vnitřní stav laděného objektu tak, že <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda v knihovně třídy .NET Framework vrátí `true` .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`Pokud <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> by metoda měla označovat, že je připojen ladicí program. `false` v opačném případě.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vracet hodnoty uvedené v následující tabulce.  
  
|Vrácená hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Laděného procesu se úspěšně aktualizoval.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Sestavení, které obsahuje metodu, není <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> načteno nebo došlo k nějaké jiné chybě, například chybějící metadata, brání jejímu rozpoznání.<br /><br /> Tato chyba je běžná a neškodná. Metodu byste měli zavolat znovu, až se načtou další sestavení.|  
|Jiné neúspěšné `HRESULT` hodnoty.|Jiné hodnoty nejspíš naznačují, že se nechovají ladicí program nebo komponenty kompilátoru.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
