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
ms.openlocfilehash: 867db3325f9b18b31f66429d01ea02be3603c0f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125765"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>ICorDebugClass::GetStaticFieldValue – metoda
Získá hodnotu zadaného statického pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 pro Pole `Def` token, který odkazuje na pole, které má být načteno.  
  
 `pFrame`  
 pro Ukazatel na objekt ICorDebugFrame, který představuje rámec, který má být použit k jednoznačnému rozlišení mezi statickými a doménovými doménami vlákna, kontextu nebo domény aplikace.  
  
 Pokud je statické pole relativní vzhledem k vláknu, kontextu nebo doméně aplikace, bude rámec určovat správnou hodnotu.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu statického pole.  
  
## <a name="remarks"></a>Poznámky  
 U parametrizovaných typů je hodnota statického pole relativní vzhledem k konkrétní instanci. Proto pokud konstruktor třídy přebírá parametry typu <xref:System.Type>, zavolejte [ICorDebugType:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) namísto `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
