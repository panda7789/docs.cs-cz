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
ms.openlocfilehash: 58a39771bd89fc9c4947f80a3c87b4d340b5461c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934872"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType – metoda
Získá pole objektů zadaného typu nebo ukazatel nebo odkaz na zadaný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Hodnota corelementtype – výčet, který určuje základní nativní typ (pole, ukazatel nebo odkaz) který se má vytvořit.  
  
 `nRank`  
 [in] Pořadí (to znamená, počet rozměrů) v poli. Tato hodnota musí být 0, pokud `elementType` Určuje typ ukazatele nebo odkazu.  
  
 `pTypeArg`  
 [in] Ukazatel na objekt ICorDebugType, který představuje typ pole, ukazatel nebo odkaz, který se má vytvořit.  
  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` typ objektu, který představuje konstruovaná pole, typ ukazatele nebo odkazu.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota *elementType* musí být jedna z následujících akcí:  
  
- TYP ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY nebo ELEMENT_TYPE_SZARRAY  
  
 Pokud hodnota *elementType* ELEMENT_TYPE_PTR nebo ELEMENT_TYPE_BYREF, *nRank* musí být nula.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
