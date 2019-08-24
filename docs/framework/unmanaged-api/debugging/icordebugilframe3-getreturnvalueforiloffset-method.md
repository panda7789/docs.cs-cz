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
ms.openlocfilehash: 5832ec095ea0e96327f6a9636193da9c0c8a5dd2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988270"
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
 Tato metoda se používá společně s metodou [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) pro získání návratové hodnoty metody. Je zvláště užitečné v případě metod, jejichž návratové hodnoty jsou ignorovány, jako v následujících dvou příkladech kódu. První příklad volá <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu, ale ignoruje návratovou hodnotu metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Druhý příklad ukazuje mnohem častější problém při ladění. Vzhledem k tomu, že metoda je použita jako argument ve volání metody, je její návratová hodnota přístupná pouze v případě, že ladicí program projde volanou metodou. V mnoha případech, zejména v případě, že je volaná metoda definována v externí knihovně, to není možné.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Pokud předáte metodu [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) , posun IL na web volání funkce, vrátí jedno nebo více nativních posunů. Ladicí program pak může nastavit zarážky na těchto nativních posunech ve funkci. Když ladicí program narazí na jednu ze zarážek, můžete předat stejný posun IL, který jste předali do této metody, a získat tak návratovou hodnotu. Ladicí program by pak měl vymazat všechny zarážky, které nastavily.  
  
> [!WARNING]
> [Metoda ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody umožňují získat informace o vrácených hodnotách pouze pro typy odkazů. Načítání informací o vrácených hodnotách z typů hodnot (tj. všechny typy, <xref:System.ValueType>které jsou odvozeny z), nejsou podporovány.  
  
 Posun IL určený `ILOffset` parametrem by měl být na webu volání funkce a laděného procesu by měl být zastaven na zarážce nastavenou v nativním posunu vráceném metodou [ICorDebugCode3:: GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) pro stejný posun IL. Pokud se laděného procesu nezastaví na správném místě pro zadaný posun IL, rozhraní API se nezdaří.  
  
 Pokud volání funkce nevrátí hodnotu, rozhraní API se nezdaří.  
  
 Tato `ICorDebugILFrame3::GetReturnValueForILOffset` metoda je k dispozici pouze v systémech založených na platformě x86 a amd64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetReturnValueLiveOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)
- [ICorDebugILFrame3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
