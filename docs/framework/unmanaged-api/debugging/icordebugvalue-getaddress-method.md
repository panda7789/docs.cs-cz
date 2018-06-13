---
title: ICorDebugValue::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c0fa19841580c7cfe8902577c3f756712a35893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420652"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress – metoda
Získá adresu tohoto objektu "ICorDebugValue", který je právě probíhá ladit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] Ukazatel na `CORDB_ADDRESS` objekt, který určuje adresu tohoto objektu hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota není k dispozici, je vrácena 0 (nula). To může nastat, pokud je hodnota aspoň částečně v registrech nebo uložené v popisovač systém uvolňování paměti (`GCHandle`).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
