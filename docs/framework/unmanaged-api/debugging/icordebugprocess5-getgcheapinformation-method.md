---
title: ICorDebugProcess5::GetGCHeapInformation – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8824ce004cac8bc2ad675c83dc6b5f167f183e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation – metoda
Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je aktuálně vyčíslitelná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHeapInfo`  
 [out] Ukazatel [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) hodnotu, která poskytuje obecné informace o kolekci halda paměti.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugProcess5::GetGCHeapInformation` Před vytváření výčtu halda musí být volána metoda nebo jednotlivé haldy oblasti zajistit, že kolekce paměti struktur v procesu jsou aktuálně platná. Kolekce halda paměti nelze proveden vaši firmu, když probíhá kolekce. Jinak hodnota výčtu může zachytit struktury kolekce paměti, které jsou neplatné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
