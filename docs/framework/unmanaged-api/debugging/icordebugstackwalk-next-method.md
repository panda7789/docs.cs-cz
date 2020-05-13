---
title: ICorDebugStackWalk::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b89e968e9b12943c8192af3b280f8bd321a02110
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378794"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next – metoda
Přesune objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) k dalšímu snímku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Modul runtime se úspěšně rozvedl do dalšího snímku (viz poznámky).|  
|E_FAIL|`ICorDebugStackWalk`Objekt nelze Upřesnit.|  
|CORDBG_S_AT_END_OF_STACK|Byl dosažen konec zásobníku v důsledku tohoto unwind.|  
|CORDBG_E_PAST_END_OF_STACK|Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 `Next`Metoda přesune `ICorDebugStackWalk` objekt do volajícího rámce pouze v případě, že modul runtime může unwind aktuální rámec. V opačném případě objekt přejde k dalšímu snímku, který může modul runtime vrátit zpět.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugStackWalk – rozhraní](icordebugstackwalk-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
