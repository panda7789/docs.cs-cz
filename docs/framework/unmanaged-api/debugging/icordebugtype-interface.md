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
ms.openlocfilehash: 8210e67f4bdd615ff65d9bd3474043fc45fd8883
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791261"
---
# <a name="icordebugtype-interface"></a>ICorDebugType – rozhraní
Představuje typ buď Basic, nebo Complex (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateTypeParameters – metoda](icordebugtype-enumeratetypeparameters-method.md)|Získá ukazatel rozhraní na ICorDebugTypeEnum, který odkazuje na Obecné parametry <xref:System.Type> třídy, na kterou odkazuje tento `ICorDebugType`.|  
|[GetBase – metoda](icordebugtype-getbase-method.md)|Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na základní třídu třídy, na kterou odkazuje tento `ICorDebugType`, pokud jedna existuje.|  
|[GetClass – metoda](icordebugtype-getclass-method.md)|Získá ukazatel rozhraní na ICorDebugClass, který odkazuje na typový konstruktor tohoto `ICorDebugType`.|  
|[GetFirstTypeParameter – metoda](icordebugtype-getfirsttypeparameter-method.md)|Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy, na kterou odkazuje tento `ICorDebugType`.|  
|[GetRank – metoda](icordebugtype-getrank-method.md)|Získá počet rozměrů v typu pole.|  
|[GetStaticFieldValue – metoda](icordebugtype-getstaticfieldvalue-method.md)|Získá ukazatel rozhraní na ICorDebugValue, který obsahuje hodnotu statického pole, na které odkazuje zadaný token pole v zadaném bloku zásobníku.|  
|[GetType – metoda](icordebugtype-gettype-method.md)|Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime <xref:System.Type>), na který odkazuje tento `ICorDebugType`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ obecný, `ICorDebugClass` představuje nevytvořený typ. Rozhraní `ICorDebugType` představuje instanci generického typu. Například hodnota hash\<K, V > by měla být reprezentována `ICorDebugClass`, zatímco zatřiďovací tabulka\<Int32, řetězec > by představovala `ICorDebugType`.  
  
 Neobecné typy jsou reprezentovány `ICorDebugClass` i `ICorDebugType`. Druhé rozhraní bylo zavedeno ve verzi .NET Framework 2,0, aby bylo možné řešit instance typu.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
