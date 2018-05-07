---
title: ICorDebugEval2::CreateValueForType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 683457c249915708becadaeda9dec265666e2023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType – metoda
Získá ukazatel na nové ICorDebugValue zadaného typu, s počáteční hodnotou nula nebo hodnotu null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pType`  
 [v] Ukazatel na ICorDebugType objekt, který představuje typ.  
  
 `ppValue`  
 [out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValueForType` Umožňuje zobecnit [icordebugeval::createvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) tím, že se k zadání typu libovolného objektu, včetně sestavený typy, jako `List<int>`. Jediným účelem: Tato metoda je ke generování hodnotu, která se dá předat do vyhodnocení funkce.  
  
 Typ musí být třídu nebo typ hodnoty. Tuto metodu nelze použít k vytvoření hodnoty pole nebo hodnoty řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
