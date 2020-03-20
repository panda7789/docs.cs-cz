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
ms.openlocfilehash: 0d1ef6c1369fd399f5b36b24a21c4b5d7f1e80fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178819"
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
 Posun IL. Viz část Poznámky.  
  
 `ppReturnValue`  
 Ukazatel na adresu objektu rozhraní "ICorDebugValue", který poskytuje informace o vrácené hodnotě volání funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) metoda získat vrácenou hodnotu metody. To je užitečné zejména v případě metod, jejichž vrácené hodnoty jsou ignorovány, jako v následujících dvou příkladech kódu. První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu, ale ignoruje vrácenou hodnotu metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Druhý příklad ilustruje mnohem častější problém v ladění. Vzhledem k tomu, že metoda se používá jako argument ve volání metody, jeho vrácená hodnota je přístupná pouze v případě, že ladicí program kroky prostřednictvím volané metody. V mnoha případech, zejména když je volaná metoda definována v externí knihovně, to není možné.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Pokud předáte [metodu ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) posunil IL do webu volání funkce, vrátí jeden nebo více nativních posunů. Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci. Když ladicí program narazí na jeden z zarážek, pak můžete předat stejný posun IL, který jste předali této metodě získat vrácenou hodnotu. Ladicí program by pak měl vymazat všechny zarážky, které nastaví.  
  
> [!WARNING]
> Metoda a `ICorDebugILFrame3::GetReturnValueForILOffset` metody [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) umožňují získat informace o vrácené hodnotě pouze pro typy odkazů. Načítání informací o vrácené hodnotě z typů hodnot <xref:System.ValueType>(tj. všechny typy, které jsou odvozeny z ) není podporováno.  
  
 Il posun zadaný `ILOffset` parametrem by měl být v lokalitě volání funkce a ladicí zařízení by mělo být zastaveno na zarážky nastavené na nativním posunu vráceném metodou [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) pro stejný posun IL. Pokud ladicí program není zastaven ve správném umístění pro zadaný posun IL, rozhraní API se nezdaří.  
  
 Pokud volání funkce nevrátí hodnotu, rozhraní API se nezdaří.  
  
 Metoda `ICorDebugILFrame3::GetReturnValueForILOffset` je k dispozici pouze v systémech x86 a AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetReturnValueLiveOffset – metoda](icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 – rozhraní](icordebugilframe3-interface.md)
