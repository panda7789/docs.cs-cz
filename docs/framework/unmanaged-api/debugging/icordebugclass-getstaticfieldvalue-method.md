---
title: ICorDebugClass::GetStaticFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d3c3c0c5634653d14577de9a1334048d75216b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue – metoda
Získá hodnotu zadaného pole statické.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fieldDef`  
 [v] Pole `Def` token, který odkazuje na pole, které mají být načteny.  
  
 `pFrame`  
 [v] Ukazatel na ICorDebugFrame objekt, který reprezentuje rámce, který se má použít k rozlišení mezi přístup z více vláken, kontext nebo statistika domény aplikace.  
  
 Pokud statické pole je relativní vzhledem ke vlákno, kontextu nebo doménu aplikace, určí rámečku správnou hodnotu.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu statického pole.  
  
## <a name="remarks"></a>Poznámky  
 Pro parametrizované typy hodnotu statických polí je relativní vzhledem ke konkrétní instance. Proto pokud konstruktoru třídy mají parametry typu <xref:System.Type>, volání [icordebugtype::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) místo `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
