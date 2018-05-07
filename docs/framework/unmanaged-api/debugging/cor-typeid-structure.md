---
title: COR_TYPEID – struktura
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cortypeid-structure"></a>COR_TYPEID – struktura
Obsahuje identifikátor typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`token1`|První token.|  
|`token2`|Druhý token.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_TYPEID` Struktura je vrácen počet ladění metody, které obsahují informace o objektech být uvolňování paměti. Ho můžete poté předat jako argument jiné ladění metody, které poskytují další informace o této položce. Například vytyčením [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objekt, je možné získat jednotlivé [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty, které představují jednotlivé objekty na spravované haldě. Potom můžete předat `COR_TYPEID` z hodnoty `COR_HEAPOBJECT.type` do [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metoda pro načtení ICorDebugType objektu, který obsahuje informace o typu o objektu.  
  
 A `COR_TYPEID` objekt má být neprůhledné. Jeho jednotlivých polí by neměly přístup ani s nimi manipulovat. Jeho jedinou použijte je jako identifikátor, který je k dispozici jako `out` parametr ve volání metody a který může být naopak předaný do jiné metody, které poskytují další informace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
