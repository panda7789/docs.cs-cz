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
ms.openlocfilehash: b27e40618d6128c21e99745ca45e139a9c21c843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988979"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType – metoda
Získá ukazatel na novou ICorDebugValue zadaného typu, s počáteční hodnotou nula nebo hodnotu null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 [in] Ukazatel na objekt, který představuje typ ICorDebugType.  
  
 `ppValue`  
 [out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValueForType` zobecňuje [icordebugeval::createvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) , neboť umožňuje určit typ libovolného objektu, včetně vytvořený typy, jako `List<int>`. Jediným účelem: Tato metoda se má generovat hodnotu, která může být předán vyhodnocení funkce.  
  
 Typ musí být třída nebo hodnotového typu. Tuto metodu nelze použít k vytvoření hodnoty pole nebo řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
