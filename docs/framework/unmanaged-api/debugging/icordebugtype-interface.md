---
title: ICorDebugType – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396693"
---
# <a name="icordebugtype-interface"></a>ICorDebugType – rozhraní
Představuje typ buď Basic, nebo Complex (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateTypeParameters – metoda](icordebugtype-enumeratetypeparameters-method.md)|Získá ukazatel rozhraní na objekt ICorDebugTypeEnum, který odkazuje na obecné <xref:System.Type> parametry třídy, na kterou odkazuje `ICorDebugType` .|  
|[GetBase – metoda](icordebugtype-getbase-method.md)|Získá ukazatel rozhraní `ICorDebugType` , který odkazuje na základní třídu třídy, na kterou odkazuje `ICorDebugType` , pokud existuje.|  
|[GetClass – metoda](icordebugtype-getclass-method.md)|Získá ukazatel rozhraní na ICorDebugClass, který odkazuje na konstruktor typu this `ICorDebugType` .|  
|[GetFirstTypeParameter – metoda](icordebugtype-getfirsttypeparameter-method.md)|Získá ukazatel rozhraní `ICorDebugType` , který odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy, na kterou odkazuje tento objekt `ICorDebugType` .|  
|[GetRank – metoda](icordebugtype-getrank-method.md)|Získá počet rozměrů v typu pole.|  
|[GetStaticFieldValue – metoda](icordebugtype-getstaticfieldvalue-method.md)|Získá ukazatel rozhraní na ICorDebugValue, který obsahuje hodnotu statického pole, na které odkazuje zadaný token pole v zadaném bloku zásobníku.|  
|[GetType – metoda](icordebugtype-gettype-method.md)|Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime), na který <xref:System.Type> odkazuje `ICorDebugType` .|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ obecný, `ICorDebugClass` představuje nevytvořený typ. `ICorDebugType`Rozhraní představuje instanci generického typu. Například zatřiďovací tabulka \< K, V> by měla být reprezentována `ICorDebugClass` , zatímco zatřiďovací tabulka \< Int32, řetězec> by představoval `ICorDebugType` .  
  
 Neobecné typy jsou reprezentovány v `ICorDebugClass` a `ICorDebugType` . Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
