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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74863af1096f8600b8095e593c1f3c820c512e9d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166800"
---
# <a name="icordebugtype-interface"></a>ICorDebugType – rozhraní
Představuje typ, základní nebo komplexní (který je definovaný uživatelem). Pokud je typ obecný, `ICorDebugType` představuje obecný typ s instancemi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateTypeParameters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Získá ukazatel rozhraní icordebugtypeenum –, který odkazuje na Obecné <xref:System.Type> parametry třída odkazovaná tímto objektem `ICorDebugType`.|  
|[GetBase – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Získá ukazatel rozhraní k `ICorDebugType` , který odkazuje na základní třídu třídy odkazuje toto `ICorDebugType`, pokud existuje.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Získá ukazatel rozhraní k ICorDebugClass, odkazující na konstruktoru typu tohoto `ICorDebugType`.|  
|[GetFirstTypeParameter – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Získá ukazatel rozhraní k `ICorDebugType` , která odkazuje na první obecný <xref:System.Type> parametr pro konstruktor třídy odkazuje toto `ICorDebugType`.|  
|[GetRank – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Získá počet dimenzí v typu pole.|  
|[GetStaticFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Získá ukazatel rozhraní k ICorDebugValue, obsahující hodnotu statické pole určené pole odkazuje tokenu v určeném zásobníku rámce.|  
|[GetType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Získá hodnotu corelementtype –, který popisuje nativní typ modulu common language runtime <xref:System.Type> odkazovaná tímto objektem `ICorDebugType`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ obecný, `ICorDebugClass` představuje typ bez instancí. `ICorDebugType` Rozhraní představuje instanci obecného typu. Například zatřiďovací tabulky\<K, V > by být reprezentována `ICorDebugClass`, zatímco zatřiďovací tabulky\<Int32, String > by být reprezentována `ICorDebugType`.  
  
 Neobecné typy jsou reprezentovány obě `ICorDebugClass` a `ICorDebugType`. Druhá možnost rozhraní byla zavedena v rozhraní .NET Framework verze 2.0 k vytvoření instance typu řešení.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
