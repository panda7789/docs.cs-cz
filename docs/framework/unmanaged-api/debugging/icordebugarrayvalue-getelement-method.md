---
title: ICorDebugArrayValue::GetElement – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 500e01955666c7a8e2bd1dcf9d34afe3aeb6b421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement – metoda
Získá hodnotu pro dané pole elementu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdim`  
 [v] Počet dimenzí tohoto `ICorDebugArrayValue` objektu.  
  
 Tato hodnota je také velikost `indices` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.  
  
 `indices`  
 [v] Pole hodnot index, z nichž každý určuje pozici v rámci dimenze `ICorDebugArrayValue` objektu.  
  
 Tato hodnota nesmí být null.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu zadaného prvku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
