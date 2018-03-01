---
title: "ICorDebugProcess5::EnumerateHeap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fabe3d70b493427f3845b5752946b00097c1e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap – metoda
Získá enumerátor pro objekty v haldě spravované.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppObject`  
 [out] Ukazatel na adresu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objekt, který je enumerátor pro objekty, které jsou umístěné na spravovaná halda.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním `ICorDebugProcess5::EnumerateHeap` metody by měly volat [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda a zkontrolujte hodnotu `areGCStructuresValid` pole vráceného objektu [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objekt, který chcete zkontrolujte, zda je vyčíslitelná kolekce halda paměti v jejím aktuálním stavu. Kromě toho `ICorDebugProcess5::EnumerateHeap` vrátí `E_FAIL` Pokud připojíte příliš brzy v doba platnosti procesu před paměti, pro spravovaná halda je přidělen.  
  
 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objekt rozhraní je standardní enumerátor odvozen z rozhraní ICorDebugEnum, který umožňuje vytvořit výčet [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty. Naplní tuto metodu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu kolekce s [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o všech objektech. Kolekce může také zahrnovat [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instancí, které obsahují informace o objektech, které nejsou root podle objektu, ale nebyly dosud shromážděných modulem garbage collector.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
