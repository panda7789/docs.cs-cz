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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d0b92dccceab48fcf0780a29d7bac38d591455
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714968"
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
  
#### <a name="parameters"></a>Parametry  
 `ILOffset`  
 Posun IL. V části poznámky.  
  
 `ppReturnValue`  
 Ukazatel na adresu objektu rozhraní "ICorDebugValue", který poskytuje informace o vrácené hodnotě volání funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metodu k získání vrácené hodnoty metody. Je to užitečné zejména v případě metod, jejichž vrácené hodnoty jsou ignorovány, stejně jako v následujících dvou příkladech. První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody, ale ignoruje vrácenou hodnotu metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Druhý příklad ukazuje mnohem častější problém v ladění. Protože metoda se používá jako argument ve volání metody, vrácená hodnota je dostupná jenom v případě, že ladicí program projde volané metody. V mnoha případech zejména pokud volaná metoda je definována v externí knihovně, která není možné.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Pokud předáte [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda posun IL na funkci volání webu, vrátí jeden nebo více nativních posunů. Ladicí program může potom nastavit zarážky u těchto nativních posunů funkce. Pokud ladicí program narazí na jednu ze zarážek, které můžete předat stejné odsazení IL, které jste předali do této metody k získání vrácené hodnoty. Ladicí program by měl poté zrušit všechny zarážky, které nastavil.  
  
> [!WARNING]
>  [ICorDebugCode3::GetReturnValueLiveOffset Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody umožňují získat informace o vrácené hodnotě pouze pro typy odkazů. Načítají se informace o vrácené hodnotě z typů hodnot (to znamená, že všechny typy, které jsou odvozeny z <xref:System.ValueType>) se nepodporuje.  
  
 Posun IL určený parametrem `ILOffset` parametr by měl být v místě volání funkce a laděný proces by měl být zastaven na zarážce nastavené pro nativní posun vrácený metodou [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) – metoda pro stejný posun IL. Pokud laděná položka není zastavená na správném umístění pro zadaný posun IL, rozhraní API se nezdaří.  
  
 Pokud volání funkce nevrací hodnotu, rozhraní API se nezdaří.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [GetReturnValueLiveOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
