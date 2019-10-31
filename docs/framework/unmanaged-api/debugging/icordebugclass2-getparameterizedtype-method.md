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
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125733"
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
 pro Hodnota výčtu CorElementType –, která určuje typ elementu pro tuto třídu: tuto hodnotu nastavte na ELEMENT_TYPE_VALUETYPE, pokud tento ICorDebugClass2 představuje typ hodnoty. Nastavte tuto hodnotu na ELEMENT_TYPE_CLASS, pokud tento `ICorDebugClass2` představuje komplexní typ.  
  
 `nTypeArgs`  
 pro Počet parametrů typu, pokud je typ obecný. Počet parametrů typu (pokud existuje) musí odpovídat číslu požadovanému třídou.  
  
 `ppTypeArgs`  
 pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje parametr typu. Pokud třída není obecná, tato hodnota je null.  
  
 `ppType`  
 mimo Ukazatel na adresu `ICorDebugType`ho objektu, který představuje deklaraci typu. Tento objekt je ekvivalentní objektu <xref:System.Type> ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud třída není obecná, to znamená, pokud nemá žádné parametry typu, `GetParameterizedType` jednoduše načte objekt typu modulu runtime odpovídající třídě. Parametr `elementType` by měl být nastaven na správný typ elementu pro třídu: ELEMENT_TYPE_VALUETYPE, pokud je třída typem hodnoty; v opačném případě ELEMENT_TYPE_CLASS.  
  
 Pokud třída přijímá parametry typu (například `ArrayList<T>`), můžete použít `GetParameterizedType` k vytvoření objektu typu pro instanci typu, jako je například `ArrayList<int>`.  
  
## <a name="background-information"></a>Základní informace  
 V .NET Framework verzích 1,0 a 1,1 může být každý typ v metadatech přímo mapován na typ v běžícím procesu. Proto typ metadat a typ modulu runtime mají v běžícím procesu jednu reprezentaci. Jeden obecný typ v metadatech však lze namapovat na mnoho různých instancí typu v běžícím procesu. Například typ metadat `SortedList<K,V>` lze namapovat na `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`a tak dále. Proto potřebujete způsob, jak zpracovat instanci typu.  
  
 .NET Framework verze 2,0 zavádí rozhraní `ICorDebugType`. Pro obecný typ objekt `ICorDebugClass` nebo `ICorDebugClass2` představuje neinstanciní typ (`SortedList<K,V>`) a objekt `ICorDebugType` představuje různé typy s vytvořenými instancemi. Pro objekt `ICorDebugClass` nebo `ICorDebugClass2` můžete vytvořit objekt `ICorDebugType` pro jakoukoliv instanci voláním metody `ICorDebugClass2::GetParameterizedType`. Můžete také vytvořit objekt `ICorDebugType` pro jednoduchý typ, jako je Int32 nebo pro neobecný typ.  
  
 Zavedení objektu `ICorDebugType`, který představuje pojem běhu typu, má v rámci rozhraní API efekt Ripple. Funkce, které dříve trvaly objekt `ICorDebugClass` nebo `ICorDebugClass2` nebo i hodnota `CorElementType`, jsou zobecněny k převzetí objektu `ICorDebugType`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
