---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975963"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a>ICorDebugExceptionObjectValue::EnumerateExceptionCallStack – metoda
Načte enumerátor do zásobníku volání vložený v objektu výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 ppCallStackEnum  
 mimo Ukazatel na adresu objektu rozhraní [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , který je enumerátor trasování zásobníku pro objekt spravované výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Pokud nejsou k dispozici žádné informace zásobníku volání, metoda `S_OK`vrátí hodnotu a [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) je platný enumerátor s délkou 0. Pokud metoda nemůže načíst informace o trasování zásobníku, návratová hodnota je `E_FAIL` a není vrácen žádný enumerátor.  
  
 Objekt [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) zodpovídá za dekódování dat trasování zásobníku z `_stackTrace` pole objektu Exception.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugExceptionObjectValue – rozhraní](icordebugexceptionobjectvalue-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
