---
title: ICorDebugArrayValue::HasBaseIndicies – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: e6e8eb91bbc41faf0dcea010da9aa54995058653
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894978"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a>ICorDebugArrayValue::HasBaseIndicies – metoda
Získá hodnotu, která označuje, zda jakékoli dimenze v tomto poli mají základní index nenulového typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbHasBaseIndicies`  
 mimo Ukazatel na logickou hodnotu, která je `true` v případě, že jeden nebo více `ICorDebugArrayValue` dimenzí tohoto objektu má základní index nenulového typu; v opačném případě je `false`logická hodnota.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]
