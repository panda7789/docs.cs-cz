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
ms.openlocfilehash: 4f3f553ed5dc93433610365e0dae5bee54863de5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129631"
---
# <a name="icordebugtype-interface"></a>ICorDebugType – rozhraní
Představuje typ buď Basic, nebo Complex (tj. definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateTypeParameters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Získá ukazatel rozhraní na ICorDebugTypeEnum, který odkazuje na Obecné parametry <xref:System.Type> třídy, na kterou odkazuje tento `ICorDebugType`.|  
|[GetBase – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na základní třídu třídy, na kterou odkazuje tento `ICorDebugType`, pokud jedna existuje.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Získá ukazatel rozhraní na ICorDebugClass, který odkazuje na typový konstruktor tohoto `ICorDebugType`.|  
|[GetFirstTypeParameter – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Získá ukazatel rozhraní na `ICorDebugType`, který odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy, na kterou odkazuje tento `ICorDebugType`.|  
|[GetRank – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Získá počet rozměrů v typu pole.|  
|[GetStaticFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Získá ukazatel rozhraní na ICorDebugValue, který obsahuje hodnotu statického pole, na které odkazuje zadaný token pole v zadaném bloku zásobníku.|  
|[GetType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime <xref:System.Type>), na který odkazuje tento `ICorDebugType`.|  
  
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

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
