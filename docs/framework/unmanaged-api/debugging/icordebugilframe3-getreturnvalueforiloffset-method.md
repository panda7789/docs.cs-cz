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
ms.openlocfilehash: 315bd78f660e093ecbf65224bd09a9b4f44300b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420931"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset – metoda
Získá objekt "ICorDebugValue", který zapouzdří návratovou hodnotu funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ILOffset`  
 Korekce IL. Najdete v části poznámky.  
  
 `ppReturnValue`  
 Ukazatel na adresu "ICorDebugValue" rozhraní objektu, který obsahuje informace o návratovou hodnotu volání funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá spolu s [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda získat návratovou hodnotu metody. Je užitečné v případě metody, jejichž návratové hodnoty jsou ignorovány, jako v následujících příkladech dvě kódu. První volání příklad <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metoda, ale ignoruje návratovou hodnotu metody.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 V druhém příkladu znázorňuje víc častých problémů při ladění. Vzhledem k tomu, že metoda se používá jako argument při volání metody, hodnoty je dostupné jenom v případě, že ladicí program prostřednictvím vyvolání metody. V mnoha případech zejména při vyvolání metody je definována v vnější knihovny, tento způsob není možný.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Pokud předáte [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) metoda na IL posun k lokalitě volání funkce vrátí jeden nebo více nativní posun. Ladicí program pak můžete nastavit zarážky na tyto nativní posuny ve funkci. Pokud se ladicí program dotkne některé zarážce, můžete pak předejte stejnou korekce IL, který je předán tuto metodu za účelem získání návratovou hodnotu. Ladicí program by měl zrušte zaškrtnutí všech zarážek, které ji nastavit.  
  
> [!WARNING]
>  [Icordebugcode3::getreturnvalueliveoffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) a `ICorDebugILFrame3::GetReturnValueForILOffset` metody vám umožňují získat informace o návratovou hodnotu pro odkazové typy pouze. Získávání informací o návratová hodnota z typů hodnot (to znamená, že všechny typy, které jsou odvozeny od <xref:System.ValueType>) není podporován.  
  
 Korekce IL určeného `ILOffset` parametr by měl být v lokalitě volání funkce a ladění by se měla zastavit na zarážce nastavit na nativní posunu vrácený [icordebugcode3::getreturnvalueliveoffset –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) – metoda pro stejný korekce IL. Pokud ve správném umístění pro zadaný korekce IL nebyla zastavena ladění, rozhraní API se nezdaří.  
  
 Pokud volání funkce nevrací hodnotu, rozhraní API se nezdaří.  
  
 `ICorDebugILFrame3::GetReturnValueForILOffset` Metoda je k dispozici pouze na základě x86 a AMD64 systémy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetReturnValueLiveOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [ICorDebugILFrame3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
