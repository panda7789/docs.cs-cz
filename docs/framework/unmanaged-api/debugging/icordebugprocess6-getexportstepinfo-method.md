---
title: ICorDebugProcess6::GetExportStepInfo – metoda
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178534"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo – metoda
Obsahuje informace o funkcích exportovaných za běhu, které vám pomohou krokovat spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametry  
 pszExportName  
 [v] Název funkce exportu za běhu, jak je napsáno v tabulce exportu PE.  
  
 invokeKind  
 [out] Ukazatel na člen a [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) výčet, který popisuje, jak exportované funkce vyvolá spravovaný kód.  
  
 invokePurpose  
 [out] Ukazatel na člena výčtu [CorDebugCodeInvokePurpose,](cordebugcodeinvokepurpose-enumeration.md) který popisuje, proč exportovaná funkce bude volat spravovaný kód.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vrátit hodnoty uvedené v následující tabulce.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Volání metody bylo úspěšné.|  
|`E_POINTER`|`pInvokeKind`nebo `pInvokePurpose` je **null**.|  
|Jiné `HRESULT` selhávající hodnoty.|Podle potřeby.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
