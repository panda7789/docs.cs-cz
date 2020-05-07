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
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894060"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType – metoda
Získá deklaraci typu pro tuto třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 pro Hodnota výčtu CorElementType –, která určuje typ elementu pro tuto třídu: nastavte tuto hodnotu na ELEMENT_TYPE_VALUETYPE, pokud tento ICorDebugClass2 představuje typ hodnoty. Nastavte tuto hodnotu na ELEMENT_TYPE_CLASS, pokud `ICorDebugClass2` tato hodnota představuje komplexní typ.  
  
 `nTypeArgs`  
 pro Počet parametrů typu, pokud je typ obecný. Počet parametrů typu (pokud existuje) musí odpovídat číslu požadovanému třídou.  
  
 `ppTypeArgs`  
 pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje parametr typu. Pokud třída není obecná, tato hodnota je null.  
  
 `ppType`  
 mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje deklaraci typu. Tento objekt je ekvivalentní <xref:System.Type> objektu ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud třída není obecná, to znamená, pokud nemá žádné parametry typu, `GetParameterizedType` jednoduše Získá objekt typu runtime odpovídající třídě. `elementType` Parametr by měl být nastaven na správný typ elementu pro třídu: ELEMENT_TYPE_VALUETYPE, pokud je třída typem hodnoty; v opačném případě ELEMENT_TYPE_CLASS.  
  
 Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` k vytvoření objektu typu pro instanci typu, jako je `ArrayList<int>`například.  
  
## <a name="background-information"></a>Základní informace  
 V .NET Framework verzích 1,0 a 1,1 může být každý typ v metadatech přímo mapován na typ v běžícím procesu. Proto typ metadat a typ modulu runtime mají v běžícím procesu jednu reprezentaci. Jeden obecný typ v metadatech však lze namapovat na mnoho různých instancí typu v běžícím procesu. Například typ `SortedList<K,V>` metadat může být namapován na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>` `SortedList<String,Array<Int32>>`, a tak dále. Proto potřebujete způsob, jak zpracovat instanci typu.  
  
 `ICorDebugType` Rozhraní .NET Framework verze 2,0 zavádí rozhraní. Pro obecný typ `ICorDebugClass` objekt nebo `ICorDebugClass2` představuje neinstanci typu (`SortedList<K,V>`) a `ICorDebugType` objekt představuje různé typy s vytvořenými instancemi. V případě `ICorDebugClass` objektu `ICorDebugClass2` nebo můžete vytvořit `ICorDebugType` objekt pro jakoukoliv instanci voláním `ICorDebugClass2::GetParameterizedType` metody. Můžete také vytvořit `ICorDebugType` objekt pro jednoduchý typ, jako je Int32 nebo pro neobecný typ.  
  
 Zavedení `ICorDebugType` objektu představujícího pojem běhového typu má v celém rozhraní API efekt Ripple. Funkce, `ICorDebugClass` které dříve trvaly `ICorDebugClass2` objekt nebo nebo i `CorElementType` hodnota, jsou zobecněny k převzetí `ICorDebugType` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
