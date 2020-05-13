---
title: Rozhraní ICorDebugProcess6
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: 4ad350e36ee15d7c1781e03698fbee3fd40c4c12
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212864"
---
# <a name="icordebugprocess6-interface"></a>Rozhraní ICorDebugProcess6
Logicky rozšiřuje rozhraní ICorDebugProcess a povoluje funkce jako dekódování spravovaných událostí ladění, které jsou zakódované v nativních událostech ladění výjimek a rozdělování virtuálních modulů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DecodeEvent – metoda](icordebugprocess6-decodeevent-method.md)|Dekóduje spravované události ladění, které byly zapouzdřeny v datové části speciálně vytvořené nativní výjimky ladění.|  
|[EnableVirtualModuleSplitting – metoda](icordebugprocess6-enablevirtualmodulesplitting-method.md)|Povolí nebo zakáže rozdělení virtuálního modulu.|  
|[GetCode – metoda](icordebugprocess6-getcode-method.md)|Načte informace o spravovaném kódu na konkrétní kódové adrese.|  
|[GetExportStepInfo – metoda](icordebugprocess6-getexportstepinfo-method.md)|Poskytuje informace o exportovaných funkcích modulu runtime, které vám pomůžou krokovat se spravovaným kódem.|  
|[MarkDebuggerAttached – metoda](icordebugprocess6-markdebuggerattached-method.md)|Změní vnitřní stav laděného objektu tak, že <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda v knihovně třídy .NET Framework vrátí `true` .|  
|[Metoda ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)|Upozorní [ICorDebug](icordebug-interface.md) , že proces běží.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Rozhraní je k dispozici pouze s .NET Native. Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
