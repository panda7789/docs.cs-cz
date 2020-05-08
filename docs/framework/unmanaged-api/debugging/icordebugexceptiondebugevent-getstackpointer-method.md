---
title: 'ICorDebugExceptionDebugEvent:: GetStackPointer – metoda'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 4f84183dfc23ebc0d0fee9feeb21329c217b9cca
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976015"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent:: GetStackPointer – metoda
Získá ukazatel zásobníku pro tuto událost ladění výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStackPointer`  
 mimo Ukazatel na adresu ukazatele zásobníku pro tuto událost ladění výjimky. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Význam tohoto ukazatele zásobníku závisí na typu události, jak je znázorněno v následující tabulce.  
  
|Typ události|Význam `pStackPointer` hodnoty|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro rámec, který vyvolal výjimku.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro rámec uživatelského kódu nejblíže k bodu vyvolané výjimky.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro rámec, který obsahuje obslužnou rutinu catch.|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pStackPointer`má **hodnotu null**.|  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
 Typ události je k dispozici z metody [ICorDebugDebugEvent:: GetEventKind –](icordebugdebugevent-geteventkind-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
