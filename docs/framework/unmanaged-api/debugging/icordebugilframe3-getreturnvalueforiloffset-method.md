---
title: ICorDebugILFrame3::GetReturnValueForILOffset – metoda
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 7a96385ccc6e7f9089365c19bb8f150015bba81c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788533"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset – metoda
Získá objekt "ICorDebugValue", který zapouzdřuje vrácenou hodnotu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ILOffset`  
 Posun IL Viz část poznámky.  
  
 `ppReturnValue`  
 Ukazatel na adresu objektu rozhraní "ICorDebugValue", která poskytuje informace o vrácené hodnotě volání funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá společně s metodou [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro získání návratové hodnoty metody. Je zvláště užitečné v případě metod, jejichž návratové hodnoty jsou ignorovány, jako v následujících dvou příkladech kódu. První příklad volá metodu <xref:System.Int32.TryParse%2A?displayProperty=nameWithType>, ale ignoruje návratovou hodnotu metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Druhý příklad ukazuje mnohem častější problém při ladění. Vzhledem k tomu, že metoda je použita jako argument ve volání metody, je její návratová hodnota přístupná pouze v případě, že ladicí program projde volanou metodou. V mnoha případech, zejména v případě, že je volaná metoda definována v externí knihovně, to není možné.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Pokud předáte metodu [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) , posun IL na web volání funkce, vrátí jedno nebo více nativních posunů. Ladicí program pak může nastavit zarážky na těchto nativních posunech ve funkci. Když ladicí program narazí na jednu ze zarážek, můžete předat stejný posun IL, který jste předali do této metody, a získat tak návratovou hodnotu. Ladicí program by pak měl vymazat všechny zarážky, které nastavily.  
  
> [!WARNING]
> [Metoda ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) a metody `ICorDebugILFrame3::GetReturnValueForILOffset` umožňují získat informace o vrácených hodnotách pouze pro typy odkazů. Načítání informací o vrácených hodnotách z typů hodnot (tj. všechny typy, které jsou odvozeny z <xref:System.ValueType>) nejsou podporovány.  
  
 Posun IL určený parametrem `ILOffset` by měl být na webu volání funkce a laděného procesu by měl být zastaven na zarážce nastavenou v nativním posunu vráceném metodou [ICorDebugCode3:: GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro stejný posun IL. Pokud se laděného procesu nezastaví na správném místě pro zadaný posun IL, rozhraní API se nezdaří.  
  
 Pokud volání funkce nevrátí hodnotu, rozhraní API se nezdaří.  
  
 Metoda `ICorDebugILFrame3::GetReturnValueForILOffset` je k dispozici pouze v systémech založených na platformě x86 a AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetReturnValueLiveOffset – metoda](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 – rozhraní](icordebugilframe3-interface.md)
