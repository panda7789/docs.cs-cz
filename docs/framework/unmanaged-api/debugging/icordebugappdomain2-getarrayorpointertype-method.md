---
title: ICorDebugAppDomain2::GetArrayOrPointerType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: 166f6bb50849df8550871958d7034fdf2a841abb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089118"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType – metoda
Získá pole zadaného typu nebo ukazatel nebo odkaz na zadaný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 pro Hodnota výčtu CorElementType –, která určuje podkladový nativní typ (pole, ukazatel nebo odkaz), který má být vytvořen.  
  
 `nRank`  
 pro Rozměr (tj. počet rozměrů) pole. Tato hodnota musí být 0, pokud `elementType` určuje typ ukazatele nebo odkazu.  
  
 `pTypeArg`  
 pro Ukazatel na objekt ICorDebugType, který představuje typ pole, ukazatel nebo odkaz, který má být vytvořen.  
  
 `ppType`  
 mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje konstruované pole, typ ukazatele nebo typ odkazu.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota typu *ElementType* musí být jedna z následujících:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY  
  
 Pokud je hodnota typu *ELEMENTTYPE* ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_BYREF, *nRank* musí být nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
