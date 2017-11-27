---
title: "ICorDebugVariableHome::GetSlotIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3eb8ed980fd523d0b0d29fbef770652a1d96146f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome::GetSlotIndex – metoda
Získá spravovaného indexu slotu místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 [out] Ukazatel na pozici indexu místní proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí následující hodnoty.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Volání metody, které vrátil hodnotu pozici indexu v `pSlotIndex`.|  
|`E_FAIL`|Aktuální [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance představuje argument funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Index slotu lze načíst metadata pro tuto místní proměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugVariableHome rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
