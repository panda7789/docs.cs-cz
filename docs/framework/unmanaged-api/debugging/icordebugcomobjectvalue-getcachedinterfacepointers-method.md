---
title: ICorDebugComObjectValue::GetCachedInterfacePointers – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: fa22c17ed7d5bcd689f21d2d855d9be7a6a8e164
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892810"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers – metoda
Načte nezpracované ukazatele rozhraní uložené v mezipaměti v aktuální obálce pro vyvolané za běhu (RCW).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 pro Hodnota, která určuje, zda bude metoda vracet pouze prostředí Windows Runtime rozhraní (`IInspectable` rozhraní) nebo všechna rozhraní COM, která jsou uložena do mezipaměti pomocí obálky volání za běhu (RCW).  
  
 `celt`  
 pro Počet objektů, jejichž adresy mají být načteny.  
  
 `pceltFetched`  
 mimo Ukazatel na počet skutečně vrácených `CORDB_ADDRESS` hodnot `ptrs`.  
  
 `ptrs`  
 Ukazatel na počáteční adresu pole `CORDB_ADDRESS` hodnot, které obsahují adresy objektů rozhraní uložených v mezipaměti.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugComObjectValue – rozhraní](icordebugcomobjectvalue-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
