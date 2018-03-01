---
title: "ICorDebugClass2::GetParameterizedType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9cbb755bd8f52482f7eece6e9d236f29cadc419
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [v] Hodnota CorElementType – výčet, který určuje typ elementu pro tuto třídu: nastavte tuto hodnotu na typ ELEMENT_TYPE_VALUETYPE, který, pokud tato ICorDebugClass2 představuje typ hodnoty. Pokud nastavením této hodnoty na ELEMENT_TYPE_CLASS `ICorDebugClass2` představuje komplexního typu.  
  
 `nTypeArgs`  
 [v] Počet parametrů typu, pokud je typ Obecné. Počet parametrů typů (pokud existuje) musí odpovídat počtu požadovaného v třídě.  
  
 `ppTypeArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který představuje typ parametru. Pokud je třída neobecnou, tato hodnota je null.  
  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje deklaraci typu. Tento objekt je ekvivalentní <xref:System.Type> objektu ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je třída neobecnou, to znamená, pokud ji nemá žádné parametry typu `GetParameterizedType` jednoduše získá odpovídající třídu objekt typu modulu runtime. `elementType` Parametr musí být nastavená na typ správné elementu pro třídu: Typ ELEMENT_TYPE_VALUETYPE, který pokud třída je typu hodnotu, jinak hodnota ELEMENT_TYPE_CLASS.  
  
 Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` vytvořit jako objekt typu pro typ instancí `ArrayList<int>`.  
  
## <a name="background-information"></a>Základní informace  
 V rozhraní .NET Framework verze 1.0 a 1.1 každý typ v metadatech přímo mapovat k typu v běžící proces. Proto typ metadat a typ modulu runtime měl jeden reprezentace v běžící proces. Jeden obecný typ v metadatech však lze mapovat na mnoha různých instancí možnosti typu v běžící proces. Například typ metadat `SortedList<K,V>` můžete namapovat `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`a tak dále. Proto musíte způsob, jak zpracovat vytvoření instance typu.  
  
 Představuje rozhraní .NET Framework verze 2.0 `ICorDebugType` rozhraní. Pro obecný typ `ICorDebugClass` nebo `ICorDebugClass2` objekt představuje typ bez instancí (`SortedList<K,V>`) a `ICorDebugType` objekt představuje různé typy instancí. Zadané `ICorDebugClass` nebo `ICorDebugClass2` objekt, můžete vytvořit `ICorDebugType` objekt pro vytváření všech instancí voláním `ICorDebugClass2::GetParameterizedType` metoda. Můžete taky vytvořit `ICorDebugType` jednoduchý typ, třeba Int32, nebo pro neobecný typ objektu.  
  
 Zavedení `ICorDebugType` objekt představující běhu představu o typu má vliv ripple v celém rozhraní API. Funkce, které dříve trvalo `ICorDebugClass` nebo `ICorDebugClass2` objektu nebo dokonce `CorElementType` hodnotu zobecněné provést `ICorDebugType` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
