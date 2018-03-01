---
title: "ICorDebugVariableHome::GetRegister – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54f1c737b0c6ce6281a71419cbd8c88277702f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome::GetRegister – metoda
Získá registrace, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRegister`  
 [out] CorDebugRegister – výčet hodnotu, která určuje registrace pro proměnné s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrátí následující hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Proměnná je v seznamu uvedené `pRegister` argument.|  
|`E_FAIL`|Proměnná se nenachází v registru nebo register relativní umístění.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [VariableLocationType – výčet](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [ICorDebugVariableHome – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
