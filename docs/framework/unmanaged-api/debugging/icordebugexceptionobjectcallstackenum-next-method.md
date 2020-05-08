---
title: ICorDebugExceptionObjectCallStackEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 6fce9f61e222d0fc1763495de162a94a7fc22689
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975976"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugExceptionObjectCallStackEnum::Next – metoda
Získá zadaný počet instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které obsahují informace z zásobníku volání objektu výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které mají být načteny.  
  
 `values`  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) .  
  
 `pceltFetched`  
 mimo Ukazatel na počet skutečně vrácených instancí [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) .  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugExceptionObjectCallStackEnum::Next – rozhraní](icordebugexceptionobjectcallstackenum-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
