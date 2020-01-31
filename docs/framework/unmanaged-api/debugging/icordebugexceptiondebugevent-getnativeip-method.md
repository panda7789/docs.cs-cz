---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP – metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788688"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>ICorDebugExceptionDebugEvent:: GetNativeIP – metoda
Získá nativní ukazatel instrukcí pro tuto událost ladění výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pIP`  
 mimo Ukazatel na ukazatel instrukcí pro tuto událost ladění výjimky. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Význam tohoto ukazatele instrukcí závisí na typu události, jak je znázorněno v následující tabulce.  
  
|Typ události|Význam `pStackPointer` hodnoty|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adresa instrukce pro zpracování chyb.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|Adresa kódu v rámci, která je označena metodou [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) , ve které by provádění pokračovalo, pokud nebyla vyvolána žádná výjimka. Výjimka může nebo nemusí způsobit jiný kód, jako je například blok catch klauzule `try/catch/finally`, který má být proveden v tomto rámci.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|Adresa kódu, kde se spuštění obslužné rutiny `catch` spustí v rámci snímku označeného metodou [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` je 0.|  
  
 Typ události je k dispozici z metody [ICorDebugDebugEvent:: GetEventKind –](icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugExceptionDebugEvent – rozhraní](icordebugexceptiondebugevent-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
