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
ms.openlocfilehash: 1be7eaeccb53e8b180aeb9492cd887f952bbaea5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485301"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement – metoda
Získá hodnotu prvku daného pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cdim`  
 [in] Počet dimenzí tohoto `ICorDebugArrayValue` objektu.  
  
 Tato hodnota je také velikost `indices` pole, protože jeho velikost se rovná počet rozměrů `ICorDebugArrayValue` objektu.  
  
 `indices`  
 [in] Pole hodnot indexu, z nichž každý určuje pozici v rámci dimenze sady `ICorDebugArrayValue` objektu.  
  
 Tato hodnota nesmí být null.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který představuje hodnotu zadaného prvku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
