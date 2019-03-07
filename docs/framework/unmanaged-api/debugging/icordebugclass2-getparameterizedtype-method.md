---
title: ICorDebugClass2::GetParameterizedType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e1734ca91fd48cc15b8dbf25f11518ed0455b6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475630"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType – metoda
Získá deklarace typu pro tuto třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Hodnota corelementtype – výčet, který určuje typ elementu pro tuto třídu: Nastavte tuto hodnotu na typ ELEMENT_TYPE_VALUETYPE, který, pokud tento icordebugclass2 – představuje typ hodnoty. Pokud tuto hodnotu nastavit na za řetězcem ELEMENT_TYPE_CLASS `ICorDebugClass2` představuje komplexního typu.  
  
 `nTypeArgs`  
 [in] Počet parametrů typu, pokud typ není obecný. Počet parametrů typu (pokud existuje) musí odpovídat počtu požadovaného třídy.  
  
 `ppTypeArgs`  
 [in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který reprezentuje parametr typu. Pokud je třída neobecnou, je tato hodnota null.  
  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje deklaraci typu. Tento objekt je ekvivalentní <xref:System.Type> objektu ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je třída neobecnou, to znamená, pokud nemá žádné parametry typu `GetParameterizedType` jednoduše načte běhový objekt type odpovídající třídu. `elementType` Parametr musí být nastavena na správný elementární typ pro třídu: Typ ELEMENT_TYPE_VALUETYPE, který pokud je hodnota typu; třída v opačném případě za řetězcem ELEMENT_TYPE_CLASS.  
  
 Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` k vytvoření objektu typu u typu tvořícího instanci jako `ArrayList<int>`.  
  
## <a name="background-information"></a>Základní informace  
 V rozhraní .NET Framework verze 1.0 a 1.1 všechny typy v metadatech přímo mapovat na typ v běžící proces. Proto typ metadat a typ prostředí runtime došlo jednotné vyjádření v běžící proces. Jednoho obecného typu v metadatech však lze mapovat na mnoha různým konkretizacím typu v běžící proces. Například typ metadat `SortedList<K,V>` můžete namapovat na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, a tak dále. Proto je třeba způsob, jak zpracovat vytvoření instance typu.  
  
 Představuje rozhraní .NET Framework verze 2.0 `ICorDebugType` rozhraní. Pro obecný typ `ICorDebugClass` nebo `ICorDebugClass2` objekt představuje typ bez instancí (`SortedList<K,V>`) a `ICorDebugType` objekt představuje různé instance. Vzhledem `ICorDebugClass` nebo `ICorDebugClass2` objektu, můžete vytvořit `ICorDebugType` objekt pro všechny instance voláním `ICorDebugClass2::GetParameterizedType` metoda. Můžete taky vytvořit `ICorDebugType` objekt pro jednoduchý typ., jako je například Int32, nebo u jiného než obecného typu.  
  
 Po zavedení služby `ICorDebugType` objekt reprezentující pojem run-time typu má zvlněný efekt v celém rozhraní API. Funkce, které dřív trval `ICorDebugClass` nebo `ICorDebugClass2` objektu nebo dokonce `CorElementType` hodnotu zobecněné provést `ICorDebugType` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
