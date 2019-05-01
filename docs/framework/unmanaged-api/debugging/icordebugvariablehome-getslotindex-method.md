---
title: ICorDebugVariableHome::GetSlotIndex – metoda
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993665"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome::GetSlotIndex – metoda
Získá spravované slotu index lokální proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 [out] Ukazatel pozice index lokální proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí následující hodnoty.  
  
|Value|Popis|  
|-----------|-----------------|  
|`S_OK`|Volání metody, které vrátil hodnotu index pozice v `pSlotIndex`.|  
|`E_FAIL`|Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) představuje instanci jako argument funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Index pozice, je možné načíst metadata pro tuto místní proměnnou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableHome – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
