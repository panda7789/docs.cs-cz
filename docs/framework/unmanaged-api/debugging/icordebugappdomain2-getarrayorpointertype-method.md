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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405822"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType – metoda
Získá zadaný typ, nebo ukazatel nebo odkaz na zadaný typ pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [v] Hodnota CorElementType – výčet, který určuje základní typ nativní (pole, ukazatel nebo odkaz) má být vytvořen.  
  
 `nRank`  
 [v] Pořadí (to znamená, počet dimenzí) pole. Tato hodnota musí být 0, pokud `elementType` Určuje typ ukazatele nebo odkaz.  
  
 `pTypeArg`  
 [v] Ukazatel na ICorDebugType objekt, který představuje typ pole, ukazatel nebo odkaz, který se má vytvořit.  
  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` typ objektu, který reprezentuje sestavené pole, ukazatel typu nebo odkaz.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota *elementType* musí mít jednu z následujících akcí:  
  
-   ELEMENT_TYPE_PTR  
  
-   TYPU ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY  
  
 Pokud hodnota *elementType* ELEMENT_TYPE_PTR nebo typu ELEMENT_TYPE_BYREF, *nRank* musí být nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
