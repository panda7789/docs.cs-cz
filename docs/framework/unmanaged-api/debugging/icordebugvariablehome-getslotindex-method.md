---
title: 'ICorDebugVariableHome:: GetSlotIndex – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790975"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome:: GetSlotIndex – metoda
Získá spravovaný index slotu místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 mimo Ukazatel na index slotu místní proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací následující hodnoty.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volání metody vrátilo hodnotu indexu slotu v `pSlotIndex`.|  
|`E_FAIL`|Aktuální instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) představuje argument funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Index slotu lze použít k načtení metadat pro tuto místní proměnnou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
